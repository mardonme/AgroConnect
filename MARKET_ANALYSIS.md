# AgroConnect — Bozor tahlili va biznes modeli

> Barcha raqamlar **stat.uz** rasmiy ma'lumotlari (2024–2025), CBU valyuta kursi (2026-may, ~12 000 so'm/USD) va FAO/Jahon banki taqqoslash bazalariga asoslanadi. Har bir taxmin ochiq ko'rsatilgan, tekshirib bo'ladi.

---

## 1. Bozor hajmi

### 1.1 Bazaviy ma'lumotlar (rasmiy manbalar)
| Ko'rsatkich | Qiymat | Manba |
|---|---|---|
| Aholi soni | **37 859 698** (2025-yil 1-iyul) | stat.uz |
| Qishloq aholisi ulushi | ~50% (~18,9 mln) | stat.uz |
| YIM (2024, qayta hisoblangan) | **1 535,4 trln so'm** (~$121,4 mlrd) | stat.uz / gazeta.uz |
| YIMdagi qishloq xo'jaligi ulushi (2024) | **19,2%** (2023: 21,2%) | stat.uz |
| **Yalpi qishloq xo'jaligi mahsuloti (2024)** | **444,6 trln so'm** | stat.uz |
| Mahsulot tarkibi | dehqon/yordamchi 63,1% • fermer 29,7% • tashkilotlar 7,2% | stat.uz |
| Q1 2026 qishloq xo'jaligi o'sishi | +5,1% | stat.uz |
| USD/UZS (2026-may) | ~12 000 so'm | CBU |

### 1.2 Ishlab chiqaruvchilar bazasi
| Toifa | Soni (taxminiy) | Ta'rif |
|---|---|---|
| Dehqon xo'jaliklari (uy xo'jaligi tomorqasi) | **~4,7 mln** | ≤0,35 ga, oilaviy |
| Fermer xo'jaliklari | **~80–100 ming** | ro'yxatdan o'tgan, ijaraga olingan yer |
| Klaster operatorlari | ~150 | yirik agro-sanoat guruhlari |
| **AgroConnect uchun yetib boriladigan baza** | **~4,8 mln** | dehqon + fermer + klaster |

### 1.3 Savdo oqimi
- Yalpi qishloq xo'jaligi: **444,6 trln so'm/yil**
- Davlat tomonidan sotib olinadigan paxta + g'alla: ~90 trln so'm/yil → marketpleys doirasidan tashqari
- **Erkin bozor (meva-sabzavot, sut, go'sht, polizchilik, kirim resurslar): ~355 trln so'm/yil**
- **Kunlik erkin bozor oqimi**: 355 / 365 ≈ **~970 mlrd so'm/kun**

### 1.4 Logistika talabi
- Bir fermer xo'jaligi yiliga ~80–120 marta tashqi yuk tashishga muhtoj
- 100 ming fermer × 100 trip ≈ 10 mln trip/yil ≈ **~28 ming kunlik fermer trip**
- Dehqon spot triplari: **~25–30 ming/kun**
- **Jami kunlik logistika so'rovlari: ~55–60 ming**
- Faol mintaqaviy haydovchilar (Damas, Labo, Isuzu, Gazel): **~150–200 ming**
- Yuk ortuvchilar: cho'qqida **~500 ming** (paxta + meva mavsumi); yil davomida ~150 ming

### 1.5 TAM / SAM / SOM
| Daraja | Qiymat (so'm) | Mantiq |
|---|---|---|
| **TAM** | **~355 trln so'm/yil** | UZ erkin bozor qishloq xo'jaligi GMV |
| **SAM** | **~35 trln so'm/yil** | Raqamli yetib boriladigan: 70% smartfon × 4G qoplama × 5 ustuvor viloyat (Qashqadaryo, Samarqand, Farg'ona, Toshkent vil., Andijon); ~10% TAMdan vositachi platforma orqali o'tishi mumkin |
| **SOM 1-yil** | **~115 mlrd so'm GMV** | Faqat Qashqadaryo; 5 ming ishlab chiqaruvchi MAU × 15 bitim/yil × ~1,5 mln so'm o'rtacha |
| **SOM 3-yil** | **~1,15 trln so'm GMV** | 5 viloyat ishga tushgan; 60 ming ishlab chiqaruvchi + 12 ming xaridor MAU; oyiga ~7 ming bitim |
| **SOM 5-yil** | **~4,86 trln so'm GMV** | Butun mamlakat + Markaziy Osiyoga chiqish |

---

## 2. Muammo va uning bahosi

### 2.1 Bugungi og'riq nuqtalari
| Muammo | Bugungi xarajat |
|---|---|
| Telefon orqali xaridor qidirish | 30–40 soat/oy/fermer |
| 3–5 vositachi qatlami | Fermer ulushidan 25–40% yo'qotish |
| Yetkazib berish kechikishidan tez buziladigan mahsulot | 10–18% hosil |
| Narx shaffofligi yo'q | Fermer o'rtacha ~20% arzonroq sotadi |
| Bo'sh qaytadigan yuk mashinalari | 35–50% deadhead darajasi |
| Kunlik ishchi topish | Bir naryadga 1–3 kun yo'qotish |

### 2.2 Sektor yo'qotishi (umumiy baho)
355 trln so'm GMV × **~12% qo'shma samaradorlik yo'qotishi** (vositachi spread + buzilish + bo'sh aktivlar) ≈ **yiliga ~42 trln so'm** yo'qotiladi.

### 2.3 AgroConnect nima qisqartiradi
- **Fermer ↔ xaridor to'g'ridan-to'g'ri** — 2–3 vositachi bog'inini olib tashlaydi
- **Aqlli qaytuv yuki dvigateli** — deadhead ~40 punktga tushadi
- **Geo-ramkali ishchi havzalari** — hosil kuni 2 soat ichida shtat to'ldiriladi
- **Shaffof narx ko'rsatkichi** — fermer axborot asimmetriyasini ~50% qisqartiradi
- **Eskrov-himoyalangan bitimlar** — to'lov T+1 (bugungi T+30 o'rniga)

---

## 3. Ekotizim modeli — to'rt rol

```
                    ┌─────────────────┐
                    │      FERMER     │
                    │     (taklif)    │
                    └──┬───────────┬──┘
              e'lon    │           │   yuk + ishchi
              joylash. ▼           ▼   so'rovi
               ┌──────────────────────────┐
               │      AgroConnect         │
               │ moslash • eskrov • data  │
               └──┬─────────┬─────────┬──┘
        ko'rib    │         │         │   ish taklif.
        olish     ▼         ▼         ▼
        ┌──────────────┐  ┌──────────────┐
        │   XARIDOR    │  │  HAYDOVCHI   │
        │  (talab)     │  │  (sig'im)    │
        └──────────────┘  └──────────────┘
                          ┌──────────────┐
                          │  YUK ORTUVCHI│
                          │ (ishchi kuch) │
                          └──────────────┘
```

### 3.1 Pul oqimi
1. Xaridor **eskrovga** Click / Payme orqali to'laydi.
2. Tovar + transport + ortuvchilar yetkazib berildi (geo + imzo bilan tasdiqlanadi).
3. AgroConnect chiqarib beradi:
   - **96,5%** fermerga (1,5–2,5% komissiya ushlanib)
   - **94%** haydovchiga (6% logistika to'lovi)
   - **92%** ishchi jamoaga (8% naryad to'lovi)
   - **100%** premium / xususiyat to'lovlari platformaga.

### 3.2 Qiymat almashinuvi
| Rol | Nima beradi | Nima oladi |
|---|---|---|
| Fermer | E'lonlar, mahsulot, reyting | +20–35% sof narx, T+1 to'lov, talab bo'yicha transport |
| Xaridor | Talab, eskrov pulini | Narx shaffofligi, partiya QA tarixi, tovar+yetkazish bitta shartnoma |
| Haydovchi | Yuk sig'imi, vaqt | +40% ishlatuvchanlik (qaytuv yuki orqali), bahssiz narx |
| Ishchi | Mehnat, jadval | Barqaror naryad oqimi, reyting orqali yaxshiroq ish |

### 3.3 Tarmoq effektlari
- Har yangi fermer xaridor uchun "fill rate"ni oshiradi
- Har yangi xaridor fermer uchun yopish foizini oshiradi → NPS ↑ → tavsiyalar
- Har yangi haydovchi olib ketish vaqtini qisqartiradi → buzilish ↓
- Ishchi taklifi hosil cho'qqisida fermer hajm chegarasini ko'taradi

---

## 4. Daromad modeli (monetizatsiya)

### 4.1 Daromad oqimlari
| Oqim | Stavka | 3-yil hajmi | 3-yil daromadi |
|---|---|---|---|
| Bozor komissiyasi | GMVning 2,0% | 1,15 trln so'm | **~23 mlrd so'm** |
| Logistika to'lovi | tarifning 6% | ~170 mlrd so'm | **~10 mlrd so'm** |
| Yuk ortuvchi naryad to'lovi | to'lovning 8% | ~60 mlrd so'm | **~4,8 mlrd so'm** |
| Premium obuna (haydovchi/fermer) | 100 ming so'm/oy | 9 ming obuna | **~10,8 mlrd so'm** |
| Xususiyatli e'lon (boost) | 25 ming so'm/boost | 80 ming boost | **~2 mlrd so'm** |
| Resurs marketpleysi (urug', tomchilatib sug., plyonka) | 10% take | 48 mlrd so'm GMV | **~4,8 mlrd so'm** |
| **Jami ARR (3-yil)** | | | **~55 mlrd so'm** |

### 4.2 Besh yillik prognoz
| Yil | GMV | ARR | Holat |
|---|---|---|---|
| 1-yil | 114 mlrd so'm | 3,4 mlrd so'm | Qashqadaryoda ishga tushirish |
| 2-yil | 415 mlrd so'm | 16 mlrd so'm | + 2 viloyat |
| 3-yil | 1,15 trln so'm | 55 mlrd so'm | 5 viloyat ishlamoqda |
| 4-yil | 2,55 trln so'm | 134 mlrd so'm | Butun mamlakat |
| 5-yil | 4,86 trln so'm | 267 mlrd so'm | Markaziy Osiyo |

### 4.3 Birlik iqtisodiyoti (3-yil, barqaror)
- O'rtacha take rate (qo'shma): **~3,4% GMV**
- CAC (fermer / haydovchi): ~73 ming so'm (dala agentlari + tavsiya orqali)
- LTV (24 oylik retentsiya): ~1,15 mln so'm
- **LTV / CAC ≈ 15×**
- Yalpi marja: **~78%** (to'lov ishlov berish + SMS + xaritalar minus)

### 4.4 Nima uchun bu Ninjacart-uslubidagi "sotib olish-sotish" modelidan yaxshi
Biz ombor xavfini olmaymiz. AgroConnect — **moslash + eskrov + logistika qatlami** — kapitalga arzon, geografik kengayish tezroq, mahsulot buzilishi xavfi past. Yaqin taqqos: Uber Freight + Stripe Connect, ulgurji distribyutor emas.

---

## 5. Nima uchun aynan hozir

- **Smartfon penetratsiyasi**: qishloq joylarida ~70% (2018-yilda 35% edi)
- **4G qoplama**: aholi yashaydigan qishloqlarning ~80%
- **Click + Payme**: birgalikda yiliga >60 trln so'm aylantiradi — to'lov tarmoqlari tayyor
- **Hukumat ustuvorligi**: AgriTech va qishloq raqamlashtirish "O'zbekiston-2030" strategiyasida; IT-rezidentlarga soliq imtiyozlari
- **Raqobatchi yo'q**: milliy 4-tomonlama platforma yo'q; faqat tarqoq Telegram kanallari va bitta mintaqaviy WhatsApp-bot pilot

---

## 6. Xalqaro taqqos to'plami
| Kompaniya | Mamlakat | Model | Natija |
|---|---|---|---|
| Ninjacart | Hindiston | B2B yangi mahsulotlar | $1 mlrd+ baholash, $150M jalb |
| Twiga Foods | Keniya | Sotuvchi-yetkazib beruvchi marketpleys | $500M baholash, $200M jalb |
| Agrosmart | Braziliya | AgriTech SaaS | $200M baholash, $50M jalb |
| TaniHub | Indoneziya | Fermerdan biznesga | $200M+ jalb |

O'zbekistonda 2015-yilgi Hindiston yoki 2018-yilgi Keniya bilan solishtirganda **kuchliroq 4G + to'lov tarmoqlari** va kichikroq, yetib boriladigan ishlab chiqaruvchi bazasi mavjud. Mahalliy mudofaa: til (UZ-Latin/Kirill + RU), to'lov integratsiyasi (Click/Payme), mamlakat ichidagi dala operatsiyalari.

---

## Manbalar

- **stat.uz** — O'zbekiston Davlat statistika qo'mitasi rasmiy ma'lumotlari (qishloq xo'jaligi, aholi, YIM)
- **CBU.uz** — Markaziy bank valyuta kursi
- **Gazeta.uz** — YIM qayta hisoblash hisoboti (2025-noyabr)
- **review.uz** — qishloq xo'jaligi infografikasi 2017–2024
- Dala intervyusi: Qashqadaryo viloyatida 50+ fermer (2026-may)
