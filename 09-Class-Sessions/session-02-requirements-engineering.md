# Session 2 — Requirements Engineering | جلسه دوم: مهندسی نیازمندی‌ها
**Textbook:** 9th ed., Chapter 7; 8th ed., Chapter 8.

## فارسی — هدف جلسه
مهندسی نیازمندی‌ها به تیم کمک می‌کند مسئله را بفهمد، افراد و سازمان‌های مرتبط را شناسایی کند، نیازهایشان را استخراج و تحلیل کند و آن‌ها را به شکلی روشن و قابل بررسی ثبت کند. نیازمندی باید برای ذی‌نفع قابل فهم، برای تیم توسعه قابل استفاده و برای آزمون قابل ارزیابی باشد.

### فعالیت‌های اصلی
1. **Inception:** شناخت مسئله، هدف، محدوده و افراد مرتبط.
2. **Elicitation:** جمع‌آوری نیاز از مصاحبه، مشاهده، جلسه، پرسش‌نامه و مستندات.
3. **Elaboration:** روشن‌کردن سناریوها، داده‌ها، رفتارها و محدودیت‌ها.
4. **Negotiation:** حل تعارض و توافق روی اولویت و محدوده واقع‌بینانه.
5. **Specification:** ثبت نیازمندی با شناسه و عبارت دقیق.
6. **Validation:** بررسی درستی، کامل‌بودن، سازگاری و آزمون‌پذیری.
7. **Requirements Management:** پیگیری تغییرها و ارتباط نیازمندی با طراحی و آزمون.

در Agile این فعالیت‌ها در طول چرخه‌های توسعه ادامه دارند و لزوماً فقط در ابتدای پروژه انجام نمی‌شوند.

### Stakeholder
ذی‌نفع، فرد یا گروهی است که بر پروژه اثر می‌گذارد یا از سیستم اثر می‌پذیرد. در TEKINO ذی‌نفعان شامل Customer، Administrator، Product Owner، Inventory Staff، Customer Support Staff، Payment Gateway، Delivery Service و Business Owner هستند.
Stakeholder با Actor یکسان نیست: Actor نقشی است که مستقیماً با سیستم تعامل می‌کند؛ بنابراین همه ذی‌نفعان الزاماً Actor نمودار Use Case نیستند.

### Functional Requirements
نیازمندی‌های کارکردی خدمات و رفتارهای سیستم را مشخص می‌کنند؛ مانند مشاهده و جست‌وجوی محصول، مدیریت سبد خرید، ارسال درخواست پرداخت و مدیریت موجودی.

### Non-Functional Requirements
نیازمندی‌های غیرکارکردی کیفیت‌ها و محدودیت‌ها را بیان می‌کنند؛ مانند Performance، Security، Reliability، Usability، Availability، Compatibility، Maintainability، Privacy و Recovery. هدف پاسخ‌گویی ۲ ثانیه و دسترس‌پذیری ۹۹٪ در TEKINO اهداف پیشنهادی‌اند و تا زمان اندازه‌گیری و آزمون، نتیجه واقعی محسوب نمی‌شوند.

## تکلیف جلسه دوم در TEKINO
**خواسته استاد:** شناسایی ذی‌نفعان و استخراج نیازمندی‌های Functional و Non-Functional.
**خروجی‌ها:** [Stakeholders](../02-Stakeholders/stakeholders.md)، [Functional Requirements](../03-Requirements/functional-requirements.md) (FR-01 تا FR-14)، [Non-Functional Requirements](../03-Requirements/non-functional-requirements.md) (NFR-01 تا NFR-12).

## English summary
Requirements engineering identifies stakeholder needs, analyzes and negotiates them, specifies requirements, validates them, and manages change. Functional requirements define system services; non-functional requirements define quality attributes and constraints. TEKINO documents eight stakeholder groups, fourteen functional requirements, and twelve proposed non-functional requirements.

## نکات ارائه
1. FR می‌گوید سیستم چه کاری انجام دهد؛ NFR می‌گوید آن کار با چه کیفیت یا محدودیتی انجام شود.
2. شناسه‌ها برای ردیابی نیازمندی در User Story، Use Case و آزمون استفاده می‌شوند.
3. نیازمندی قابل سنجش، امکان ارزیابی عینی‌تری دارد.
4. Stakeholder مفهوم گسترده‌تری از Actor دارد.