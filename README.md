# Flipper Alpha - ملفات KiCad

ملفات مولّدة من صور المخطط والـ PCB المرفوعة:
- `Flipper_Alpha.kicad_sch`  المخطط الكامل (KiCad 8)
- `Flipper_Alpha.kicad_pcb`  لوحة جاهزة للتوصيل (KiCad 8)

الرموز (Symbols) والـ Footprints **مدمجة داخل الملفات نفسها** - لا تحتاج أي مكتبات خارجية.

## خريطة التوصيلات (Pin Mapping)

| الوحدة | الإشارة | ESP32 (CYD) | ملاحظة |
|---|---|---|---|
| PN532 (I2C) | SDA / SCL | GPIO21 / GPIO22 | تغذية 3.3V |
| CC1101 (SPI) | SCK / MISO / MOSI | GPIO18 / GPIO19 / GPIO23 | Shared SPI |
| CC1101 | CSN / GDO0 / GDO2 | GPIO5 / GPIO2 / GPIO35 | |
| NRF24L01 (SPI) | SCK / MISO / MOSI | GPIO18 / GPIO19 / GPIO23 | Shared SPI |
| NRF24L01 | CE / CSN | GPIO26 / GPIO25 | |
| IR LED | خرج | GPIO4 عبر مقاومة 220Ω | LED إلى GND |
| TSOP (IR RX) | OUT | GPIO34 | |
| 433MHz RF | TX / RX | GPIO12 / GPIO13 | تغذية 5V |
| GPS (UART) | TX / RX | GPIO16 / GPIO17 | UART2 |

## افتراضات مهمة (راجعها قبل التصنيع!)
1. بعض الشبكات في الصورة الأصلية غير واضحة تماماً - استخدمت أكثر تعيين منطقي (مطابق للـ Flipper Zero التقليدي).
2. الـ PCB **غير موصول (Unrouted)**: المكونات موضوعة والشبكات (Nets) جاهزة - افتح KiCad ووجّه المسارات يدوياً أو باستخدام FreeRouting.
3. تحقق من Pinout نسخة شاشتك CYD-24325028 بالضبط قبل الطباعة.
4. J1-J4 (موصلات XH) تركت بدون توصيل - عيّنها حسب احتياج الـ Buttons/Expansion في الـ firmware.
5. أبعاد اللوحة 125x85mm مع 4 ثقوب تثبيت M3.

## خطوات العمل في KiCad
1. افتح `Flipper_Alpha.kicad_sch` -> تحقق من ERC
2. افتح `Flipper_Alpha.kicad_pcb` -> اضغط B لتحديث الأرضي، ثم وصّل الشبكات
