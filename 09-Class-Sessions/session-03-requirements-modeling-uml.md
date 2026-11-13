# Session 3 — Requirements Modeling and UML | جلسه سوم: مدل‌سازی نیازمندی‌ها و UML
**Textbook:** 9th ed., Chapter 8; 8th ed., Chapters 9–11.

## فارسی — هدف جلسه
مدل‌سازی نیازمندی‌ها، رفتار سیستم و ارتباط آن با بازیگران را از دیدگاه‌های مختلف نشان می‌دهد. UML زبان مدل‌سازی استانداردی است؛ نمودارها جایگزین متن نیازمندی نیستند، بلکه به فهم و کشف ابهام کمک می‌کنند.

### Use Case Diagram
- **Actor:** نقش بیرونی نسبت به سیستم، مانند Customer یا Payment Gateway.
- **Use Case:** هدف یا خدمتی که سیستم ارائه می‌کند، مانند Browse Products.
- **System Boundary:** محدوده سیستم؛ موارد کاربرد درون آن و Actorها بیرون آن قرار می‌گیرند.
- **Association:** ارتباط Actor با Use Case.
- **<<include>>:** رفتار الزامی و مشترکی که Use Case پایه از آن استفاده می‌کند.
- **<<extend>>:** رفتار افزوده و شرطی که در شرایط خاص به Use Case پایه اضافه می‌شود.

### Activity Diagram
این نمودار جریان فعالیت‌ها، تصمیم‌ها و مسیرهای جایگزین را نشان می‌دهد.
- Initial Node: شروع فرایند.
- Action: انجام یک فعالیت.
- Decision/Merge: انشعاب یا ادغام مسیرها.
- Control Flow: ترتیب جریان.
- Activity Final: پایان فعالیت.
- Swimlane: مسئولیت هر فعالیت را به نقش یا بخش مربوط نسبت می‌دهد.

## تکلیف جلسه سوم در TEKINO
**خواسته استاد:** رسم Use Case و Activity Diagram فرایند اصلی.
در Use Case، بازیگران Customer، Administrator و Payment Gateway شناسایی شده‌اند. Activity Diagram خرید محصول را از مشاهده و انتخاب کالا تا ورود، بررسی سبد و موجودی، محاسبه مبلغ و پردازش پرداخت مدل می‌کند. مسیر پرداخت ناموفق، تلاش مجدد یا لغو خرید را نشان می‌دهد. طبق FR-10، سفارش نهایی پس از تأیید موفقیت پرداخت ایجاد می‌شود.
**خروجی:** [Use Case Analysis](../07-UML/use-case-analysis.md)، [Use Case Diagram](../07-UML/use-case-diagram.svg)، [Activity Diagram](../07-UML/activity-diagram.svg)، [Notes](../07-UML/activity-diagram-notes.md).

## English summary
The Use Case Diagram captures system actors and their goals. The Activity Diagram models the main purchase flow, including authentication, cart and stock validation, payment processing, and success/failure paths. The payment gateway is an external actor; failed payment must not be treated as a successful paid order.

## نکات ارائه
1. Use Case هدف‌ها و تعامل‌ها را نمایش می‌دهد، نه ترتیب زمانی کامل را.
2. Activity Diagram ترتیب فعالیت‌ها و تصمیم‌ها را نشان می‌دهد.
3. پیکان Include به سمت Use Case واردشونده است.
4. Swimlane مسئولیت هر فعالیت را مشخص می‌کند.