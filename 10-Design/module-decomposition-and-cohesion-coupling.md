# Module Decomposition and Cohesion/Coupling Analysis — TEKINO

## 1. Purpose | هدف

This document decomposes the proposed TEKINO e-commerce system into logical modules and evaluates their responsibilities using two fundamental design concepts: cohesion and coupling.

این سند سیستم فروشگاه TEKINO را به ماژول‌های منطقی تقسیم می‌کند و کیفیت مرزبندی آن‌ها را با دو مفهوم اصلی طراحی، یعنی انسجام درونی (Cohesion) و وابستگی بین ماژول‌ها (Coupling)، بررسی می‌کند.

## 2. Design Principles | اصول طراحی

### Modularity — ماژولار بودن
A module is a cohesive unit that owns a defined responsibility and communicates with other modules through explicit contracts. Modularity helps limit the impact of change and makes the system easier to understand and maintain.

ماژول بخشی از سیستم است که مسئولیت مشخصی دارد و از طریق قراردادهای روشن با بخش‌های دیگر ارتباط می‌گیرد. ماژول‌بندی باعث می‌شود فهم سیستم، توسعه، آزمون و نگهداری آن ساده‌تر شود.

### Cohesion — انسجام درونی
Cohesion describes how strongly the elements inside a module contribute to the same purpose. The design goal is high cohesion: each module should have a focused responsibility.

Cohesion نشان می‌دهد اجزای داخل یک ماژول چقدر برای یک هدف مشترک به هم مرتبط هستند. هدف طراحی، انسجام بالا است؛ یعنی هر ماژول مسئولیت متمرکز داشته باشد.

### Coupling — وابستگی بین ماژول‌ها
Coupling describes the degree of dependency between modules. The design goal is low coupling: one module should not need to know another module's internal implementation details.

Coupling میزان وابستگی بین ماژول‌ها را نشان می‌دهد. هدف طراحی، وابستگی کم است؛ یعنی یک ماژول برای استفاده از ماژول دیگر مجبور نباشد از جزئیات داخلی آن آگاه شود.

## 3. Proposed TEKINO Modules | ماژول‌های پیشنهادی

| Module / ماژول | Main responsibility / مسئولیت اصلی | Example elements / نمونه اجزا |
|---|---|---|
| Catalog | Product listing, search, filtering and details / فهرست، جست‌وجو، فیلتر و جزئیات محصول | ProductCatalogService, Product |
| Identity & Access | Registration, login and authorization / ثبت‌نام، ورود و مجوزها | AuthenticationService, Customer |
| Shopping Cart | Adding, removing and changing cart items / مدیریت اقلام سبد خرید | CartService, CartItem |
| Order | Checkout coordination and order lifecycle / هماهنگی خرید و چرخه سفارش | OrderService, Order |
| Payment | Payment initiation and transaction result handling / شروع و بررسی نتیجه پرداخت | PaymentService, IPaymentGateway |
| Inventory | Stock, availability and reservation / موجودی، دسترس‌پذیری و رزرو | InventoryService, InventoryItem |
| Administration | Administrative product and order operations / عملیات مدیریتی محصول و سفارش | ProductAdminService, OrderAdminService |
| Persistence | Data storage and retrieval / ذخیره‌سازی و بازیابی داده | Repository implementations |

## 4. Qualitative Cohesion and Coupling Review | تحلیل کیفی

| Design example / مثال طراحی | Cohesion | Coupling | Reason / دلیل |
|---|---|---|---|
| InventoryService only owns stock operations / سرویس فقط عملیات موجودی را انجام می‌دهد | High / بالا | Low–Medium / کم تا متوسط | Focused responsibility and a small contract / مسئولیت روشن و قرارداد محدود |
| OrderService depends on repository and payment interfaces / سرویس سفارش به Interface وابسته است | High / بالا | Low / کم | Depends on contracts, not vendor internals / وابستگی به قرارداد، نه جزئیات فروشنده |
| One class handles search, payment, inventory and login / یک کلاس مسئول تمام قابلیت‌ها باشد | Low / پایین | High / بالا | Unrelated responsibilities and broad dependencies / مسئولیت‌های نامرتبط و وابستگی گسترده |
| Multiple modules directly call a provider-specific payment SDK / چند ماژول مستقیماً SDK درگاه را صدا بزنند | Medium or Low / متوسط یا پایین | High / بالا | Provider-specific details spread across the system / پخش شدن جزئیات درگاه در کل سیستم |

These are qualitative design judgments based on the proposed boundaries. No numerical cohesion or coupling metrics have been calculated from source code because the system has not been implemented.

این ارزیابی بر اساس مرزبندی پیشنهادی انجام شده است. چون سیستم هنوز پیاده‌سازی نشده، هیچ معیار عددی Cohesion یا Coupling از کد واقعی محاسبه نشده است.

## 5. Module Interaction | ارتباط ماژول‌ها

- Catalog reads product information through product repositories.
- Shopping Cart uses Catalog data and checks stock through Inventory.
- Order coordinates checkout, cart validation, inventory reservation and payment.
- Payment communicates with the external payment provider through IPaymentGateway.
- Administration uses catalog, inventory and order services under role-based access control.
- Persistence implements repository contracts used by the application.

ترجمه مسیر تعامل: کاتالوگ اطلاعات محصول را در اختیار بخش‌های دیگر می‌گذارد؛ سبد خرید برای بررسی موجودی از Inventory استفاده می‌کند؛ Order فرایند Checkout، اعتبارسنجی، رزرو موجودی و پرداخت را هماهنگ می‌کند؛ Payment از طریق Interface با درگاه بیرونی ارتباط دارد؛ بخش مدیریت نیز سرویس‌های محصول، موجودی و سفارش را با کنترل دسترسی فراخوانی می‌کند.

## 6. Design Decision | تصمیم طراحی

For the current academic scope, TEKINO is modeled as a **modular monolith**: logical modules are separated, but they may run within one deployable application. This keeps the architecture understandable and avoids introducing distributed-system complexity without a demonstrated need.

با توجه به محدوده فعلی پروژه، TEKINO به‌صورت یک **Modular Monolith** مدل می‌شود؛ یعنی ماژول‌ها از نظر مسئولیت و کد تفکیک می‌شوند، اما می‌توانند در یک برنامه واحد اجرا شوند. در شرایط فعلی، نیازی اثبات‌شده برای تبدیل هر ماژول به یک Microservice مستقل نداریم.

## 7. Deliverable and Limitations | خروجی و محدودیت

- Diagram: [SVG preview](module-decomposition.svg) · [editable draw.io source](module-decomposition.drawio)
- Related requirements: FR-01 to FR-14.
- This is a logical design proposal, not implemented source code.
- The proposed boundaries should be reviewed if new requirements or technology constraints are introduced.

این خروجی یک پیشنهاد طراحی منطقی است، نه کد پیاده‌سازی‌شده. در صورت اضافه شدن نیازمندی یا محدودیت فنی جدید، مرزبندی ماژول‌ها باید بازبینی شود.
