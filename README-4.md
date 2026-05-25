# KYMO PWA — O'rnatish Qo'llanmasi

## 1. FIREBASE LOYIHA YARATISH

1. https://console.firebase.google.com ga kiring
2. **"Add project"** → loyiha nomini kiriting (masalan: `kymo-olimpiada`)
3. Google Analytics: **o'chirish mumkin**
4. **"Create project"** ✅

---

## 2. AUTHENTICATION SOZLASH

1. Firebase Console → **Authentication** → **Get started**
2. **Sign-in method** → **Email/Password** → Enable qiling → Save

---

## 3. FIRESTORE DATABASE YARATISH

1. Firebase Console → **Firestore Database** → **Create database**
2. **"Start in production mode"** → Next
3. Location: **europe-west** yoki **us-central** (ixtiyoriy)
4. **Enable** ✅

### Security Rules yuklash:
1. Firestore → **Rules** tab
2. `firestore.rules` faylidagi matnni ko'chiring va joylashtiring
3. **"admin@kymo.uz"** o'rniga **o'z emailingizni** yozing
4. **Publish** ✅

---

## 4. WEB APP QO'SHISH & CONFIG OLISH

1. Firebase Console → **Project Settings** (⚙️) → **Your apps**
2. **"</>"** (Web) tugmasini bosing
3. App nickname: `kymo-web` → **Register app**
4. Ko'rsatilgan **firebaseConfig** ni nusxa oling

### index.html ga config qo'yish:
`index.html` fayldagi quyidagi qismni **o'z config'ingiz bilan almashtiring**:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",          // ← bu yerga
  authDomain: "...",               // ← bu yerga
  projectId: "...",                // ← va boshqalar
  ...
};

const ADMIN_EMAIL = "admin@kymo.uz"; // ← O'Z EMAILINGIZ
```

---

## 5. GITHUB PAGES GA DEPLOY QILISH

1. GitHub → **New repository** → nom bering (masalan: `kymo`)
2. Fayllarni yuklang: `index.html`, `manifest.json`, `sw.js`
3. Repository → **Settings** → **Pages**
4. Source: **Deploy from a branch** → `main` → `/root`
5. **Save** ✅

Sayt manzili: `https://SIZNING_USERNAME.github.io/kymo/`

---

## 6. FIREBASE AUTHORIZED DOMAINS

GitHub Pages domeningizni Firebase ga qo'shing:
1. Firebase → Authentication → Settings → **Authorized domains**
2. **"Add domain"** → `SIZNING_USERNAME.github.io`

---

## 7. ADMIN SIFATIDA KIRISH

- Siz `ADMIN_EMAIL` da ko'rsatilgan email bilan kirsangiz
- Dashboard da **"Admin panel"** tugmasi paydo bo'ladi
- Barcha o'quvchilarning natijalarini ko'rasiz
- CSV yuklab olish imkoniyati bor

---

## XAVFSIZLIK HAQIDA

✅ Har bir o'quvchi FAQAT o'z natijasini ko'ra oladi
✅ Natijani bir marta topshirish mumkin (qayta urinib bo'lmaydi)
✅ Natijani o'zgartirish mumkin emas (Firestore rules)
✅ Admin barcha natijalarni ko'ra oladi
✅ Parollar Firebase tomonidan shifrlangan

---

## SINOV SAVOLLARI QO'SHISH / O'ZGARTIRISH

`index.html` dagi `QUESTIONS` obyektini tahrirlang:
```javascript
const QUESTIONS = {
  3: [ // 3-sinf savollari
    {
      q: "Savol matni?",
      opts: ["A variant", "B variant", "C variant", "D variant"],
      ans: 2  // ← to'g'ri javob indeksi (0,1,2,3)
    },
    // ...
  ],
  4: [...], // 4-sinf
  5: [...]  // 5-sinf
};
```

---

## MUAMMO CHIQSA

- **"Permission denied"** → Firestore Rules ni tekshiring
- **"Firebase not configured"** → firebaseConfig ni tekshiring  
- **Sayt ochilmasa** → GitHub Pages settings ni tekshiring
- **Login ishlamasa** → Authentication → Email/Password enabled ekanini tekshiring
