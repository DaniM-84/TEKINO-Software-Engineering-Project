# Layered Architecture — TEKINO

## 1. Purpose | هدف

This document proposes a layered architecture for the TEKINO e-commerce system and explains the responsibility of each layer, the dependency direction, and the boundaries between internal components and external services.

در این سند معماری لایه‌ای پیشنهادی TEKINO معرفی می‌شود. هدف، جداسازی مسئولیت رابط کاربری، هماهنگ‌سازی سناریوهای کاربردی، قواعد کسب‌وکار و جزئیات فنی ذخیره‌سازی و ارتباط با سرویس‌های بیرونی است.

## 2. Proposed Layers | لایه‌های پیشنهادی

### Presentation Layer — لایه نمایش
**Responsibility:** Customer-facing pages and the administration interface. It collects input, displays results, and communicates with application use cases.

**مسئولیت:** نمایش رابط فروشگاه و پنل مدیریت، دریافت ورودی کاربر و نمایش نتیجه. منطق اصلی قیمت، موجودی، سفارش و پرداخت نباید در این لایه قرار گیرد.

Examples: Product Catalog Page, Product Details Page, Cart Page, Checkout Page, Login Page, Admin Dashboard.

### Application Layer — لایه کاربرد
**Responsibility:** Orchestrates application use cases and coordinates domain services. It handles the workflow of searching, managing a cart, submitting checkout, and managing administrative actions.

**مسئولیت:** اجرای جریان سناریوها و هماهنگی سرویس‌های دامنه؛ مانند جست‌وجو، تغییر سبد خرید، ثبت سفارش و عملیات مدیریتی.

Examples: SearchProductsUseCase, UpdateCartUseCase, CheckoutUseCase, ManageProductUseCase.

### Domain / Business Layer — لایه دامنه و کسب‌وکار
**Responsibility:** Contains core business rules and domain behavior. It should remain independent of presentation frameworks and provider-specific infrastructure.

**مسئولیت:** نگهداری قواعد اصلی فروشگاه، مانند اعتبارسنجی سبد، وضعیت سفارش، محاسبه مبلغ، شرایط موجودی و قواعد مربوط به پرداخت. این لایه باید تا حد ممکن از فناوری رابط کاربری و ارائه‌دهنده خارجی مستقل باشد.

Examples: Product, Cart, Order, Payment, Inventory policies; CartService, OrderService, InventoryService.

### Infrastructure Layer — لایه زیرساخت
**Responsibility:** Implements technical details and adapters for databases and external providers.

**مسئولیت:** پیاده‌سازی جزئیات فنی شامل Repositoryهای پایگاه داده، Adapter درگاه پرداخت و اتصال به سرویس‌های بیرونی.

Examples: SqlProductRepository, SqlOrderRepository, PaymentGatewayAdapter, EmailNotificationAdapter.

## 3. Dependency Direction | جهت وابستگی

The intended dependency direction is:

**Presentation → Application → Domain**

Infrastructure provides implementations for interfaces required by the inner application/domain logic. The core business rules should not import a provider-specific payment SDK or depend directly on a database driver.

جهت اصلی درخواست از Presentation به Application و سپس به Domain است. زیرساخت، قراردادهایی را پیاده‌سازی می‌کند که بخش‌های داخلی نیاز دارند. منطق اصلی کسب‌وکار نباید مستقیماً به SDK یک درگاه یا Driver پایگاه داده وابسته شود.

## 4. Example Checkout Flow | نمونه جریان ثبت سفارش

1. The customer submits checkout from the Presentation layer.
2. CheckoutUseCase in the Application layer coordinates the process.
3. Domain services validate cart contents, product availability, and order rules.
4. An inventory contract is used to reserve the required stock.
5. IPaymentGateway is called through an adapter to initiate and verify payment.
6. After successful payment confirmation, the order is persisted through IOrderRepository.
7. The Application layer returns the result to the Presentation layer.

ترجمه: مشتری درخواست نهایی‌سازی خرید را ارسال می‌کند؛ Use Case مربوط به Checkout فرایند را هماهنگ می‌کند؛ قواعد دامنه سبد و موجودی را اعتبارسنجی می‌کنند؛ موجودی رزرو می‌شود؛ پرداخت از طریق Adapter انجام و نتیجه آن بررسی می‌شود؛ سپس پس از تأیید موفقیت پرداخت، سفارش ذخیره و نتیجه به رابط کاربری بازگردانده می‌شود.

## 5. Why This Architecture? | دلیل انتخاب

For the current single-vendor e-commerce scope, a layered modular application is a reasonable initial design because it separates user-interface concerns, workflow coordination, business rules, and infrastructure. It is understandable for the academic project and supports future change without requiring microservices.

برای محدوده فعلی یک فروشگاه تک‌فروشنده‌ای، معماری لایه‌ای یک انتخاب اولیه قابل دفاع است؛ چون مسئولیت‌ها را از هم جدا می‌کند و برای پروژه دانشگاهی قابل ارائه است. این انتخاب به معنی آن نیست که معماری‌های دیگر نامناسب‌اند. تصمیم نهایی در پروژه واقعی به بار سیستم، امنیت، هزینه، فناوری و مهارت تیم وابسته است.

## 6. Limitations | محدودیت‌ها

- The architecture is a design proposal; no running application is claimed.
- The exact database, programming framework, and payment provider have not been selected.
- Transaction handling, idempotency, concurrency, and security details need further design before implementation.
- The diagram is conceptual and does not specify deployment topology.

این معماری پیشنهادی است؛ هنوز فناوری پایگاه داده، چارچوب برنامه‌نویسی یا شرکت پرداخت انتخاب نشده و جزئیات فنی تراکنش، درخواست تکراری و هم‌زمانی باید پیش از پیاده‌سازی تکمیل شوند.

## 7. Diagram | نمودار

[Open layered-architecture.svg](layered-architecture.svg)
