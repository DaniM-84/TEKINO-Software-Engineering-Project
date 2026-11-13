# Session 5 — Software Architecture and Layered Design | جلسه پنجم: معماری لایه‌ای
**Textbook:** 9th ed., Chapters 10–11; 8th ed., Chapters 13–14.

## فارسی — هدف جلسه
معماری نرم‌افزار ساختار کلان سیستم را مشخص می‌کند: اجزای اصلی چیست، چه مسئولیتی دارند و چگونه ارتباط می‌گیرند. این تصمیم‌ها بر کیفیت‌هایی مانند امنیت، کارایی، توسعه‌پذیری و نگهداری اثر می‌گذارند.

### لایه‌های پیشنهادی TEKINO
1. **Presentation:** رابط مشتری و پنل مدیریت؛ نمایش داده و دریافت درخواست. منطق اصلی کسب‌وکار نباید در این لایه پیاده‌سازی شود.
2. **Application:** هماهنگ‌سازی سناریوها؛ مانند جست‌وجو، مدیریت سبد و ثبت سفارش.
3. **Domain / Business:** قواعد اصلی محصول، موجودی، قیمت، سفارش و پرداخت.
4. **Infrastructure:** جزئیات ذخیره‌سازی، Repositoryها و Adapterهای سرویس‌های خارجی مانند درگاه پرداخت.

### جریان وابستگی
درخواست از Presentation به Application می‌رود؛ Application از قواعد Domain استفاده می‌کند. ارتباط با پایگاه داده یا سرویس خارجی از طریق Interfaceهای مشخص انجام می‌شود و Infrastructure آن قراردادها را پیاده‌سازی می‌کند. این جداسازی، منطق اصلی را از جزئیات فناوری مستقل‌تر می‌کند.

### Component و Interface
کامپوننت واحد طراحی با مسئولیت مشخص است. Interface قرارداد ارتباطی آن را تعریف می‌کند: نام عملیات، ورودی، خروجی و شرایط خطا. Interfaceهای پروژه قراردادهای طراحی و شبه‌کد هستند، نه API پیاده‌سازی‌شده.

نمونه‌ها:
- IProductRepository: جست‌وجو و بازیابی محصول.
- IInventoryRepository: خواندن و تغییر موجودی.
- ICartRepository: ذخیره و بازیابی سبد.
- IOrderRepository: ذخیره و بازیابی سفارش.
- IPaymentGateway: شروع پرداخت و بررسی نتیجه تراکنش.
- IAuthenticationService: ثبت‌نام، ورود و بررسی هویت.
- IOrderService: هماهنگی فرایند سفارش و مشاهده وضعیت.

### چرا معماری لایه‌ای؟
برای فروشگاه تک‌فروشنده‌ای TEKINO، معماری لایه‌ای انتخاب مقدماتی مناسبی برای جدا کردن UI، منطق کسب‌وکار و ذخیره‌سازی است و برای پروژه آموزشی به‌راحتی قابل توضیح است. این انتخاب قطعی یا اثبات‌شده نیست؛ معماری نهایی باید با توجه به فناوری، بار، امنیت، هزینه و مهارت تیم ارزیابی شود.

## تکلیف جلسه پنجم
**خواسته استاد:** رسم نمودار Layered Architecture و تعریف Interface کامپوننت‌ها.
**خروجی‌ها:** [نمودار معماری](../11-Architecture/layered-architecture.svg)، [توضیح معماری](../11-Architecture/layered-architecture.md)، [قرارداد Interfaceها](../11-Architecture/component-interfaces.md).

## English summary
The proposed architecture separates TEKINO into Presentation, Application, Domain/Business, and Infrastructure layers. Application use cases coordinate domain behavior. Infrastructure provides adapters for persistence and external services. Component interfaces define operations and data contracts. These are design artifacts, not proof of implementation.

## نکات ارائه
1. معماری ساختار کلان سیستم است؛ طراحی کامپوننت جزئیات واحدهای داخلی را مشخص می‌کند.
2. Presentation مسئول نمایش و دریافت درخواست است، نه قواعد کسب‌وکار.
3. Domain قوانین اصلی فروشگاه را نگهداری می‌کند.
4. Interface قرارداد است و Adapter جزئیات ارتباط با فناوری بیرونی را پیاده می‌کند.