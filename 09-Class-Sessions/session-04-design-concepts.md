# Session 4 — Design Concepts, Modularity, Cohesion and Coupling | جلسه چهارم: طراحی و ماژول‌بندی
**Textbook:** 9th ed., Chapter 9; 8th ed., Chapter 12.

## فارسی — هدف جلسه
طراحی نرم‌افزار راه‌حل را سازمان‌دهی می‌کند و مشخص می‌سازد اجزای سیستم چه مسئولیت‌هایی دارند. ماژولار بودن یعنی تقسیم سیستم به بخش‌هایی با مسئولیت مشخص، به‌گونه‌ای که فهم، توسعه، آزمون و نگهداری آسان‌تر شود.

### ماژول (Module)
یک واحد طراحی نسبتاً مستقل با مسئولیت روشن است که از طریق رابط‌های مشخص با بخش‌های دیگر ارتباط دارد. ماژول‌ها در TEKINO براساس قابلیت‌های کسب‌وکار تعریف شده‌اند.

### Cohesion — انسجام درونی
میزان مرتبط بودن وظایف داخل یک ماژول را نشان می‌دهد.
- **High Cohesion:** اعضای ماژول برای هدفی روشن و مشترک کار می‌کنند.
- **Low Cohesion:** ماژول وظایف نامرتبط زیادی را کنار هم جمع می‌کند.
مثال مناسب: InventoryService فقط قواعد موجودی، دسترس‌پذیری و رزرو را مدیریت کند.
مثال نامناسب: GeneralManager هم‌زمان پرداخت، موجودی، جست‌وجو، احراز هویت و ارسال را انجام دهد.

### Coupling — وابستگی بین ماژول‌ها
میزان وابستگی یک ماژول به جزئیات ماژول دیگر را نشان می‌دهد.
- **Low Coupling:** ارتباط از طریق قراردادهای روشن و پایدار انجام می‌شود.
- **High Coupling:** ماژول‌ها از جزئیات داخلی یکدیگر آگاه‌اند و تغییر یک بخش، تغییرات زنجیره‌ای ایجاد می‌کند.
مثال مناسب: OrderService به قرارداد IPaymentGateway وابسته باشد، نه SDK یک شرکت خاص.
مثال نامناسب: فراخوانی مستقیم API و کوئری دیتابیس یک ارائه‌دهنده در چند ماژول مختلف.

## تفکیک پیشنهادی ماژول‌های TEKINO
| ماژول | مسئولیت |
|---|---|
| Catalog | فهرست، جست‌وجو، فیلتر و جزئیات محصول |
| Identity & Access | ثبت‌نام، ورود و کنترل دسترسی |
| Shopping Cart | افزودن، حذف و تغییر تعداد کالا |
| Order | هماهنگی خرید و چرخه سفارش |
| Payment | آغاز و بررسی نتیجه پرداخت |
| Inventory | موجودی، دسترس‌پذیری و رزرو |
| Administration | عملیات مدیریتی محصول و سفارش |
| Persistence | ذخیره‌سازی و بازیابی داده |

این تقسیم‌بندی یک مدل منطقی است و به معنی Microservice بودن سیستم نیست. برای پروژه فعلی، Modular Monolith انتخاب ساده‌تر و قابل‌کنترل‌تری است.

## تحلیل کیفی
| مثال | Cohesion | Coupling | علت |
|---|---|---|---|
| InventoryService محدود به عملیات موجودی | بالا | پایین تا متوسط | مسئولیت روشن |
| OrderService با استفاده از Interfaceها | بالا | پایین | وابستگی به قرارداد |
| کلاس واحد برای همه قابلیت‌ها | پایین | بالا | مسئولیت‌های نامرتبط |
| اتصال مستقیم تمام بخش‌ها به SDK درگاه | متوسط/پایین | بالا | وابستگی به فناوری مشخص |

این تحلیل کیفی است؛ روی کد واقعی، اندازه‌گیری عددی انجام نشده است.

## تکلیف جلسه چهارم
**خواسته استاد:** تفکیک سیستم به ماژول‌ها و تحلیل Cohesion و Coupling.
**خروجی:** [گزارش ماژول‌بندی](../10-Design/module-decomposition-and-cohesion-coupling.md) و [نمودار ماژول‌ها](../10-Design/module-decomposition.svg).

## English summary
Modularity divides a system into units with focused responsibilities. High cohesion keeps related behavior together; low coupling limits dependencies on other modules' implementation details. TEKINO is logically decomposed into Catalog, Identity & Access, Shopping Cart, Order, Payment, Inventory, Administration, and Persistence modules. It is a proposed modular-monolith design, not an implemented microservice system.

## نکات ارائه
1. Cohesion داخل یک ماژول را می‌سنجد؛ Coupling ارتباط بین ماژول‌ها را.
2. طراحی مطلوب معمولاً Cohesion بالا و Coupling پایین دارد.
3. Interface وابستگی به قرارداد را جایگزین وابستگی به جزئیات می‌کند.
4. تقسیم ماژولی به معنی توزیع‌شدن سیستم در چند سرویس نیست.