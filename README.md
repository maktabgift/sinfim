# Sinf daftari

Bu brauzerda ishlaydigan o‘quv jurnali: o‘qituvchilar davomat va baholarni yuritadi, o‘quvchilar esa o‘z natijalarini ko‘radi. HTML, CSS va JavaScript fayllari tayyor; yig‘ish yoki npm paketlarini o‘rnatish talab qilinmaydi. Ma’lumotlar brauzerning IndexedDB bazasida saqlanadi; avvalgi `localStorage` ma’lumotlari avtomatik ko‘chiriladi va mahalliy zaxira saqlanadi. IndexedDB mavjud bo‘lmagan muhitda mahalliy zaxira ishlatiladi.

## Loginlar, o‘quvchilar va baholar bazasi

Dasturchining **Bazalar** bo‘limida loginlar reyestri, o‘quvchilar va baholar alohida ko‘rinadi. IndexedDB ichida ular `logins`, `students`, `grades` bo‘limlariga yoziladi; boshqa jurnal sozlamalari `journal` bo‘limida saqlanadi. Loginni band qilish va o‘quvchi/baholarni saqlash bitta tranzaksiyada bajariladi.

Yangi o‘quvchining ism-familiyasi yozilganda `ali.valiyev` kabi login avtomatik yaratiladi. Band bo‘lsa, `ali.valiyev.2`, `ali.valiyev.3` variantlari tanlanadi. Loginni qo‘lda ham tahrirlash mumkin, lekin u ism va familiyaga mos bo‘lishi kerak. Mavjud eski loginlar avtomatik almashtirilmaydi.

Berilgan login reyestrdan o‘chirilmaydi: o‘quvchi o‘chirilsa, arxivlansa yoki loginini o‘zgartirsa ham boshqa hisobga qayta berilmaydi. Katta-kichik harflar bir xil hisoblanadi; nuqta, chiziqcha va raqamlar farqlanadi. JSON eksport reyestrni ham saqlaydi; import uning eski yozuvlarini o‘chirmaydi.

Bu baza shu brauzer va manzilga tegishli. Brauzerning barcha sayt ma’lumotlari tozalansa, mahalliy reyestr ham yo‘qolishi mumkin; uzoq muddatli saqlash uchun JSON zaxirasini olib boring. Boshqa qurilmalarda umumiy login bandligini saqlash uchun server bazasi talab qilinadi.

## VS Code’da ishga tushirish

1. `maktabgift.code-workspace` faylini VS Code’da oching.
2. Tavsiya etilgan **Live Server** kengaytmasini o‘rnating.
3. `index.html` faylini o‘ng tugma bilan bosib, **Open with Live Server** ni tanlang.
4. Ilova `http://127.0.0.1:5500/index.html` manzilida ochiladi.

Live Server ishlab turganda **F5** orqali tayyor **Sinf daftari — Edge** sozlamasi bilan JavaScript kodini kuzatish mumkin. Live Server faqat fayllarni mahalliy manzilda ochib beradi; u ma’lumotlarni serverga saqlamaydi.

Ilovani `index.html` faylini brauzerda ochish orqali ham ishlatish mumkin. Ma’lumotlar brauzer va manzilga bog‘liq: `file://`, `localhost` va `127.0.0.1` xotiralari alohida. Avvalgi yozuvlarni ko‘rish uchun avval ishlatilgan brauzer va manzilni oching; boshqa manzilga ko‘chirishda ilovaning mavjud JSON eksport/importidan foydalaning.

## Kirish

O‘quvchi, o‘qituvchi yoki dasturchi kirish oynasida mavjud login va parolingizdan foydalaning. Alohida dastlabki sozlash yoki o‘zini ro‘yxatdan o‘tkazish ekrani yo‘q. O‘quvchilarni o‘qituvchi yoki dasturchi qo‘shadi. Muvaffaqiyatli kirish sessiyasi 12 soat saqlanadi; **Chiqish** sessiyani o‘chiradi.

## O‘qituvchi rollari

- **Sinf rahbari** o‘z sinfidagi o‘quvchilar va davomatni boshqaradi.
- **Fan o‘qituvchisi** faqat biriktirilgan sinf-fan juftligida baho kiritadi.

Dasturchi sinflar, biriktirmalar, o‘quv reja va dars jadvallarini boshqaradi.

## Baholar va o‘quvchilarni joylash

Yangi o‘rnatmalarda baholar 1–10 oralig‘ida kiritiladi. Eski 2–5 sozlamasi 1–10 ga o‘tadi; mavjud baholar o‘zgartirilmaydi.

Dasturchi **O‘quvchilarni joylash** bo‘limida `student_id, full_name, class, username, password_hash` ustunli CSV faylni import qilishi mumkin. Mavjud o‘quvchi `student_id` bo‘yicha yangilanadi; baho va davomat saqlanadi. Faylda bo‘lmagan o‘quvchilarni arxivlash ixtiyoriy.

**Baholarni import qilish** bo‘limida CSV va XLSX fayllari ustunlarni moslash va oldindan ko‘rish orqali import qilinadi. XLSX uchun SheetJS kutubxonasi shu ekran ochilganda CDN orqali yuklanadi; bu imkoniyat internet talab qiladi. CSV importi uchun ushbu kutubxona kerak emas. O‘qituvchi faqat o‘ziga biriktirilgan sinf-fan juftligiga baho saqlay oladi.

## Loyiha fayllari

- `index.html` — sahifa karkasi.
- `styles.css` — dizayn va moslashuvchan ko‘rinish.
- `script.js` — kirish, sessiya, rollar, baholar, davomat, reyting, import va boshqaruv mantiqi.
- `sample-import.csv` — baholar uchun namunaviy CSV.
- `sample-curriculum.csv` — o‘quv reja uchun namunaviy CSV.
- `maktabgift.code-workspace` — VS Code ish maydoni va Edge kuzatuv sozlamasi.

## Ma’lumotlar xavfsizligi

Ma’lumotlar shu brauzerning mahalliy xotirasida saqlanadi va boshqa qurilmalarga sinxronlanmaydi. Parollar SHA-256 xesh ko‘rinishida saqlanadi. Bu prototip haqiqiy o‘quvchi ma’lumotlarini saqlash uchun mo‘ljallanmagan; real ma’lumotlar uchun server tomonidagi autentifikatsiya, ruxsat nazorati va himoyalangan ma’lumotlar bazasi kerak.
