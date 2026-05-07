# AgroConnect — Texnik topshiriq (TZ)

Versiya 0.1 · Egasi: ta'sischi jamoa · Holat: MVPgacha bo'lgan rejalashtirish

---

## 1. Texnologik stack

| Qatlam | Texnologiya | Sababi |
|---|---|---|
| Mobil ilovalar | **Flutter 3.x** (iOS + Android, bitta kod bazasi) | Bitta jamoa ikki do'konga chiqaradi; native-ga yaqin samaradorlik; Riverpod / Bloc |
| Backend API | **Node.js 20 + Fastify, TypeScript** | Yuqori o'tkazuvchanlik, oz operatsiya; TS kontraktlar Flutter bilan OpenAPI orqali bo'linadi |
| Realtime | Socket.IO + Redis adapter | Chat, haydovchiga ish push, e'lon lentalari |
| Asosiy DB | **MongoDB 7** | Moslashuvchan e'lon sxemalari, geo-so'rovlar (`2dsphere`), Atlas hududda yaxshi |
| Kesh + navbatlar | Redis 7 (BullMQ) | Rate-limit, OTP, eskrov holat mashinasi, push fan-out |
| Qidiruv | MongoDB Atlas Search yoki Meilisearch | Faceted e'lon qidirish, UZ + RU xato-bardoshli |
| Obyekt saqlash | S3-mos (Backblaze B2 / Wasabi) | Surat, KYC hujjatlari, signed URL |
| To'lov | **Click, Payme, Uzcard** SDK | Mahalliy tarmoqlar; eskrov ichki defter |
| Xaritalar | **Yandex Maps** | UZda yo'l va manzil qoplamasi eng yaxshi |
| Push | FCM + APNs | |
| SMS / OTP / fallback | **Eskiz.uz** | Smartfoni yo'q foydalanuvchilar uchun bot |
| Infratuzilma | Docker → Hetzner (EU); Cloudflare CDN; Atlas (eu-central) | |
| Kuzatuv | OpenTelemetry → Grafana Cloud; Sentry | |

---

## 2. Rollar va ruxsatlar

| Rol | Asosiy imkoniyat |
|---|---|
| **Fermer** | E'lon joylash, takliflarni qabul qilish, transport / ishchi so'rash, daromadni yechib olish |
| **Xaridor** (klient) | Ko'rish, buyurtma berish, talab e'lonlari, yetkazishni boshqarish |
| **Haydovchi** | Sig'im profili, transport ishlarini qabul qilish, qaytuv yuk lentasi |
| **Yuk ortuvchi / jamoa boshlig'i** | Jamoani boshqarish, naryadlarni qabul qilish, to'lovni taqsimlash |
| **Admin** | KYC ko'rib chiqish, nizolarni hal qilish, kontent moderatsiyasi, tahlilot |

Bir foydalanuvchi bir vaqtda bir nechta rolga ega bo'lishi mumkin (fermer o'z mashinasini ham haydashi mumkin).

---

## 3. Funksional xarita

### Fermer
- 2 daqiqalik e'lon oqimi: surat, ekin, miqdor, birlik, narx, viloyat
- Taklif / qarshi-taklif inboksi
- E'longa biriktirilgan logistika so'rovi vidjeti
- Ekin kalendari + mintaqaviy narx tarixi
- Hamyon (eskrov ushlash + bank/Humo kartaga yechib olish)

### Xaridor
- Faceted qidirish (ekin, viloyat, miqdor, narx oralig'i, organik bayrog'i, hosil sanasi)
- Teskari e'lon ("Juma kuniga 20 t pomidor kerak")
- Yirik buyurtma — bir nechta fermerga avto-bo'linadi
- Har fermer bo'yicha QA / partiya tarixi

### Haydovchi
- Sig'im profili (mashina turi, tonna/m³, sovutgich bayrog'i, o'qlar)
- Radius ichidagi ish heatmap'i
- **Qaytuv yuk dvigateli** — uy mintaqasi tomon ketayotgan kiruvchi e'lonlarni ko'rsatadi
- Daromad paneli, haftalik to'lov

### Yuk ortuvchi
- Jamoa profili (o'lcham, kuch tier, jihoz)
- Naryad kalendari
- Avto bo'linish — to'lov jamoa a'zolari hamyoniga

### O'tkir-kesuvchi (cross-cutting)
- Har bitim uchun real-vaqtli chat
- Ikki tomonlama 5-yulduzli reyting + teg-asosli fikr
- Ko'p til: UZ-Lotin, UZ-Kirill, RU
- **Offline-birinchi**: idempotency key bilan navbat, ulanish qaytsa sinxronlashadi
- **SMS bot** USSD-uslubdagi menyu — internet yo'qlar uchun

---

## 4. Foydalanuvchi oqimlari

### A oqim — Fermer mahsulot sotadi
1. Fermer e'lon joylaydi → marketpleys
2. Bir nechta xaridor taklif yuboradi → fermer qabul qiladi → eskrov to'ldiriladi
3. Fermer logistika so'rovi biriktiradi → radius ichida haydovchi mos keladi
4. Haydovchi olib chiqadi; ortuvchi jamoa olish/yetkazish nuqtasida ishlaydi
5. Geo-tasdiqlangan yetkazish → eskrov chiqariladi → reyting almashinadi

### B oqim — Xaridor talab joylaydi
1. Xaridor talab e'lonini joylaydi (miqdor, viloyat, muddat, narx shifti)
2. Dvigatel mos fermerlarga xabar yuboradi (ekin × viloyat × mavsum)
3. Fermerlar narx taklif qiladi → xaridor tanlaydi → A oqim 3-qadamidan davom

### C oqim — Haydovchi qaytuv yuk
1. Haydovchi X mintaqasida ishni tugatadi
2. Dvigatel uy mintaqasiga ketayotgan chiquvchi e'lonlarni ko'rsatadi
3. Haydovchi qabul qilganda kamaytirilgan komissiya (4% — 6% o'rniga)

### D oqim — Yuk ortuvchi naryadi
1. Fermer yoki haydovchi N nafar ortuvchi so'raydi (joy/vaqt)
2. Radius ichidagi mavjud jamoalarga push
3. Jamoa boshlig'i qabul qiladi → to'lov eskrovga oldindan kiritiladi
4. Geo + foto check-in → bajarilganda eskrov chiqadi

---

## 5. Ekranlar (mobil)

```
Auth         Telefon OTP → rol tanlash → KYC (hujjat surati)
Bosh sahifa  Rolga xos lenta (e'lonlar / ishlar / naryadlar)
E'lonlar     Ro'yxat, batafsil, yaratish, tahrirlash
Buyurtmalar  Faol, tarix, nizo
Logistika    Ochiq ishlar, mening ishlarim, marshrut, daromad
Ortuvchilar  Ochiq naryadlar, jamoa, jadval
Chat         Kanallar, xabarlar, ilovalar
Hamyon       Balans, yechib olish, to'ldirish, tranzaksiya
Profil       KYC holati, reyting, til, sozlamalar
```

---

## 6. API tuzilmasi

REST + WebSocket. Versiya: `https://api.agroconnect.uz/v1/`. JSON, JWT bearer.

### Autentifikatsiya
```
POST /auth/otp/request    { phone }
POST /auth/otp/verify     { phone, code } → { accessToken, refreshToken }
POST /auth/refresh
POST /auth/logout
```

### E'lonlar
```
GET    /listings?crop=&region=&priceMin=&priceMax=&page=
POST   /listings
GET    /listings/:id
PATCH  /listings/:id
DELETE /listings/:id
POST   /listings/:id/offers           # xaridor narx taklif qiladi
POST   /offers/:id/accept             # fermer qabul qiladi → buyurtma + eskrov
POST   /offers/:id/reject
```

### Buyurtmalar
```
GET    /orders?role=
GET    /orders/:id
POST   /orders/:id/dispute
POST   /orders/:id/confirm-delivery
```

### Logistika
```
POST   /logistics/jobs
GET    /logistics/jobs?radius=&truck=
POST   /logistics/jobs/:id/accept
POST   /logistics/jobs/:id/complete
GET    /logistics/return-loads
```

### Yuk ortuvchi naryadlari
```
POST   /gigs
GET    /gigs?date=&region=
POST   /gigs/:id/accept
POST   /gigs/:id/complete
```

### Hamyon
```
GET    /wallet
POST   /wallet/topup            { provider: 'click'|'payme', amount }
POST   /wallet/payout           { destination, amount }
GET    /wallet/transactions
```

### Realtime (Socket.IO namespaces)
```
/chat        room: deal:<id>          events: message, read, typing
/logistics   room: driver:<id>        events: job.new, job.cancelled
/feed        room: region:<code>      events: listing.new, demand.new
```

---

## 7. MongoDB sxemasi

```js
// users
{
  _id, phone, roles: ['farmer'|'client'|'driver'|'loader'],
  name, region, district, geoHome: { type:'Point', coordinates:[lng,lat] },
  kyc: { status:'pending'|'approved'|'rejected', docs:[{ type, url }] },
  rating: { avg, count },
  premium: { tier:'free'|'plus'|'pro', expiresAt },
  walletId,
  createdAt, lastSeenAt
}

// listings
{
  _id, farmerId, crop, variety, qtyKg, unitPriceUZS,
  region, district, geo: { type:'Point', coordinates:[lng,lat] },
  photos: [String],
  harvestedAt, organic:Boolean,
  status:'open'|'reserved'|'sold'|'expired',
  boost: { active, until },
  createdAt
}

// offers
{ _id, listingId, clientId, qtyKg, pricePerKgUZS, message,
  status:'pending'|'accepted'|'rejected'|'withdrawn', createdAt }

// orders
{
  _id, listingId, farmerId, clientId, qtyKg, totalUZS,
  escrow: { state:'pending'|'held'|'released'|'refunded', txnIds:[String] },
  logisticsJobId, loaderGigId,
  status:'created'|'in_transit'|'delivered'|'disputed'|'closed',
  createdAt, deliveredAt
}

// logistics_jobs
{
  _id, orderId, originGeo, destGeo, distanceKm,
  truckType:'damas'|'labo'|'isuzu'|'gazelle'|'kamaz',
  weightKg, fareUZS,
  driverId, status, returnLoadOf:ObjectId,
  createdAt, completedAt
}

// gigs (yuk ortuvchi)
{
  _id, orderId, locationGeo, headcount, hours, payoutUZS,
  teamId, status, scheduledAt, checkInAt, completedAt
}

// chats / messages
{ _id, dealId, participants:[ObjectId], lastMessageAt }
{ _id, chatId, senderId, body, attachments:[Url], readBy:[ObjectId], createdAt }

// ratings
{ _id, fromUserId, toUserId, orderId, stars, tags:[String], comment, createdAt }

// wallets / transactions (barcha summalar UZSda)
{ _id, userId, balanceUZS, holdUZS }
{ _id, walletId, type:'topup'|'payout'|'escrow_hold'|'escrow_release'|'commission',
  amountUZS, provider:'click'|'payme'|'internal', status, ref, createdAt }
```

### Indekslar
- `listings { region:1, crop:1, status:1, createdAt:-1 }`, `2dsphere` — `geo`
- `logistics_jobs` `2dsphere` — `originGeo`, `{ status:1, truckType:1 }`
- `orders { farmerId:1, createdAt:-1 }`, `{ clientId:1, createdAt:-1 }`
- `messages { chatId:1, createdAt:-1 }`
- `users { phone:1 }` unique

> Eslatma: barcha pul maydonlari **so'mda** (UZS, butun son sifatida — tiyin bilan 100 ga ko'paytirib saqlanadi). USDga konvertatsiya faqat tahlil qatlamida.

---

## 8. Funksional bo'lmagan talablar

| Soha | Maqsad |
|---|---|
| API p95 kechikishi | < 300 ms |
| Realtime yetkazish | < 1 s p95 |
| Offline mutatsiya navbati | Idempotency-Key header, qayta urinish |
| KYC tasdiqlash vaqti | < 24 soat admin SLA |
| PII shifrlash | Mongo CSFLE — telefon, KYC hujjatlar |
| Rate limit | 60 so'rov/min/foydalanuvchi; 5 OTP/soat/telefon |
| Backup | Atlas continuous + kunlik snapshot, 30 kunlik saqlash |
| Uptime | 99,5% (1-yil), 99,9% (2-yil) |

---

## 9. Yo'l xaritasi (45 kunlik MVP → 1-yil)

| Hafta | Yetkaziluvchi |
|---|---|
| 1–2 | Auth, rol onboarding, profil, KYC |
| 3 | E'lon CRUD + qidirish, surat yuklash |
| 4 | Taklif + eskrov holat mashinasi; Click/Payme |
| 5 | Logistika ishlari + haydovchi ekrani |
| 6 | Ortuvchi naryadlari, reyting, chat |
| 7 (post-MVP) | Qaytuv yuk dvigateli, SMS bot, tahlilot |
| Q2–Q4 | Premium tier, kirim resurslari marketpleysi, mintaqaviy kengayish |

---

## 10. Ochiq texnik qarorlar

- Eskrov defteri: ichki qurish vs bank bilan hamkorlik → tezlik uchun **ichki defter + Click/Payme bilan moslashuv**
- Qidiruv: Atlas Search vs Meilisearch → Atlasdan boshlash, oyiga $400 dan oshsa migratsiya
- Haydovchiga push: Socket.IO sticky vs FCM → ilova ochiq bo'lsa Socket.IO, yopiq bo'lsa FCM
- KYC tekshirish: dastlabki 6 oy admin qo'lda, keyin **MyID** integratsiyasi
