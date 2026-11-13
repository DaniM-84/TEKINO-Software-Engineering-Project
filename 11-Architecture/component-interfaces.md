# Component Interface Contracts — TEKINO

## 1. Purpose | هدف

This document defines proposed component contracts for the TEKINO architecture. An interface specifies what a component offers without exposing how it performs the work.

این سند قراردادهای پیشنهادی کامپوننت‌های TEKINO را مشخص می‌کند. Interface تعیین می‌کند یک کامپوننت چه عملیاتی را ارائه می‌دهد، چه ورودی و خروجی‌ای دارد و چه خطاهایی ممکن است برگرداند؛ اما جزئیات پیاده‌سازی را آشکار نمی‌کند.

**Important:** The definitions below are design-level pseudocode. They are not compiled source code, deployed APIs, or tested integrations.

## 2. Interface Design Rules | قواعد طراحی

- Keep each interface focused on one responsibility.
- Use meaningful operation names and explicit input/output types.
- Return clear success and error results.
- Do not expose database tables, provider SDK objects, or internal domain state to UI components.
- Use stable contracts to reduce coupling between modules.

ترجمه: هر Interface باید مسئولیت متمرکز داشته باشد؛ نام عملیات، نوع ورودی و خروجی روشن باشد؛ خطاها صریح باشند؛ جزئیات پایگاه داده یا SDK درگاه به لایه نمایش نشت نکند؛ قراردادها باید پایدار باشند تا وابستگی ماژول‌ها کاهش یابد.

## 3. Proposed Interfaces | اینترفیس‌های پیشنهادی

### 3.1 IProductRepository
**Purpose:** Retrieve product information for catalog use cases.

| Operation | Input | Output |
|---|---|---|
| getById | productId: ProductId | Product or NotFound |
| search | query: SearchQuery, filters: ProductFilters, page: PageRequest | Page<ProductSummary> |
| listCategories | none | Category[] |

کاربرد: بازیابی محصول، جست‌وجو و فهرست دسته‌بندی‌ها. این قرارداد جزئیات SQL یا نوع پایگاه داده را مشخص نمی‌کند.

### 3.2 IInventoryRepository
**Purpose:** Read stock and manage inventory reservations.

| Operation | Input | Output |
|---|---|---|
| getAvailability | productId: ProductId | Availability |
| reserve | orderId: OrderId, items: OrderItem[] | ReservationResult |
| release | reservationId: ReservationId | Result |

کاربرد: بررسی موجودی و رزرو/آزادسازی آن. قواعد زمان انقضای رزرو و رقابت هم‌زمان باید هنگام پیاده‌سازی دقیق‌تر شوند.

### 3.3 ICartRepository
**Purpose:** Persist and retrieve a customer's cart.

| Operation | Input | Output |
|---|---|---|
| getByCustomerId | customerId: CustomerId | Cart or NotFound |
| save | cart: Cart | Result |
| remove | customerId: CustomerId | Result |

### 3.4 IOrderRepository
**Purpose:** Persist orders and retrieve their status.

| Operation | Input | Output |
|---|---|---|
| createPending | order: PendingOrder | OrderId |
| markPaid | orderId: OrderId, paymentReference: PaymentReference | Result |
| getById | orderId: OrderId | Order or NotFound |
| listForCustomer | customerId: CustomerId, page: PageRequest | Page<OrderSummary> |

نکته طراحی: ایجاد سفارش در وضعیت Pending و تغییر وضعیت آن پس از تأیید پرداخت باید با سیاست تراکنش و یکپارچگی داده هماهنگ شود. این سند جزئیات پیاده‌سازی تراکنش را تعیین نمی‌کند.

### 3.5 IPaymentGateway
**Purpose:** Communicate with an external payment provider through a provider-independent contract.

| Operation | Input | Output |
|---|---|---|
| initiatePayment | orderId: OrderId, amount: Money, callbackUrl: URL | PaymentInitiationResult |
| verifyPayment | providerToken: PaymentToken | PaymentVerificationResult |

The result must contain a transaction reference and an explicit status. The adapter must validate the provider response before the order is treated as paid.

نتیجه باید وضعیت روشن و شناسه تراکنش داشته باشد. Adapter قبل از اینکه سفارش پرداخت‌شده محسوب شود باید پاسخ ارائه‌دهنده را بررسی کند.

### 3.6 IAuthenticationService
**Purpose:** Authenticate a customer and register an account.

| Operation | Input | Output |
|---|---|---|
| register | RegistrationData | CustomerId or ValidationError |
| authenticate | Email, Password | AuthResult |
| authorize | Principal, Permission | Boolean |

Password values must never be returned by this interface or stored as plaintext. Secure credential handling must be designed and verified during implementation.

### 3.7 IOrderService
**Purpose:** Coordinate the customer order workflow.

| Operation | Input | Output |
|---|---|---|
| checkout | CustomerId, CartId, ShippingAddress | CheckoutResult |
| getOrderStatus | CustomerId, OrderId | OrderStatus or AccessDenied |

The service coordinates cart validation, stock checks, payment, and order status. It must ensure that only the authenticated owner or an authorized staff member can access an order.

## 4. Example Contract Flow — Checkout | نمونه جریان

1. Presentation submits customer checkout data to the application use case.
2. The application calls IOrderService.
3. The service reads the cart using ICartRepository.
4. It checks product stock through IInventoryRepository.
5. It obtains a payment initiation result through IPaymentGateway.
6. It verifies the returned payment status before recording the final paid state.
7. It stores and returns the order result through IOrderRepository.

## 5. Error Handling | مدیریت خطا

Possible result states include ValidationError, NotFound, InsufficientStock, PaymentDeclined, PaymentVerificationFailed, AccessDenied, and TemporaryServiceUnavailable. Exact error codes and retry policy must be refined once the technology stack is selected.

## 6. Traceability | ردیابی

| Interface | Related requirements |
|---|---|
| IProductRepository | FR-01, FR-02, FR-03, FR-04 |
| IAuthenticationService | FR-05, FR-06 |
| ICartRepository | FR-07 |
| IOrderService | FR-08, FR-10, FR-11 |
| IPaymentGateway | FR-09 |
| IInventoryRepository | FR-13 |
| IOrderRepository | FR-10, FR-11, FR-14 |

## 7. Limitations | محدودیت‌ها

These contracts describe design intent only. No implementation language, database schema, concrete API endpoint, or payment vendor has been selected. The contracts should be refined before coding and updated when requirements change.

این Interfaceها قرارداد طراحی هستند. زبان پیاده‌سازی، ساختار پایگاه داده، Endpoint واقعی و ارائه‌دهنده پرداخت هنوز انتخاب نشده‌اند؛ بنابراین پیش از کدنویسی باید جزئیات آن‌ها تکمیل و با تغییر نیازمندی‌ها بازبینی شوند.
