# Mazzeka — Waiter Call V1

نسخة أولى مستقلة لنظام نداء الويتر عبر QR.

## V1
- QR مستقل لكل ترابيزة (1–20).
- العميل يرى رقم الترابيزة وزر «اطلب الويتر» فقط.
- 60 ثانية cooldown بعد الطلب.
- الطلب يصل لحظيًا إلى Dashboard عبر Firestore.
- Dashboard محمي بـ Firebase Authentication.
- صوت عربي من سماعات الكمبيوتر: «الترابيزة رقم X تطلب الويتر» ثلاث مرات.
- الطلب يبقى ظاهرًا حتى الضغط على «تم».
- لا يوجد تطبيق هاتف، POS، حسابات ويتر، Analytics أو Push Notifications.

## إعداد Firebase
1. أنشئ Firebase Project مستقل باسم Mazzeka.
2. فعّل Firestore Database.
3. فعّل Authentication > Email/Password.
4. أنشئ حساب الدخول الخاص بالـ Dashboard.
5. انسخ Web App config إلى `config.js`.
6. طبّق `firestore.rules` من Firebase Console أو Firebase CLI.

> لا تضع Service Account أو أي secret داخل الموقع. Web API key الخاص بتطبيق Firebase Web ليس سرًا، والحماية الفعلية هنا من Firestore Rules + Authentication.

## التشغيل
يمكن نشر المجلد مباشرة على Vercel. لا يوجد build step.

- العميل: `/?table=17`
- Dashboard: `/dashboard.html`
- طباعة QR: `/qr.html`

## ملاحظة الصوت
عند أول فتح للـ Dashboard اضغط «تفعيل الصوت» مرة واحدة بسبب قيود المتصفح على التشغيل الصوتي التلقائي. بعد ذلك اترك الصفحة مفتوحة على كمبيوتر الكافيه والسماعات متصلة به.

خفض موسيقى الكافيه نفسها تلقائيًا غير داخل V1 لأن الموقع لا يملك تحكمًا موثوقًا في مستوى صوت برامج أخرى مثل Spotify/YouTube أو Windows Master Volume.
