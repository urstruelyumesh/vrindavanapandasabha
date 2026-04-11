# श्री बृजवासी पंडा सभा — QR System Setup Guide
## GitHub Pages + Google Sheets (100% Free)

---

## 📦 आपके Project में क्या है?

```
panda-sabha/
├── purohit.html   ← QR स्कैन करने पर यह खुलता है (सार्वजनिक)
├── admin.html     ← Admin panel (सिर्फ आपके लिए)
└── SETUP_GUIDE.md ← यह फाइल
```

---
---

# PART 1 — Google Sheet बनाएं (Database)

## Step 1 — Google Sheet खोलें

1. **sheets.google.com** खोलें (Google account से login करें)
2. **"+ Blank"** दबाकर नई sheet बनाएं
3. Sheet का नाम दें: `Purohit Data`

---

## Step 2 — Headers डालें (EXACTLY यही लिखें)

**Row 1 में यह headers डालें** (बिल्कुल यही spelling):

| A | B | C | D | E | F | G | H | I | J |
|---|---|---|---|---|---|---|---|---|---|
| enrollmentNo | formNo | name | fatherName | age | gotra | address | dehri | phone | photoURL |

---

## Step 3 — Sample Data डालें

**Row 2 से असली डेटा भरें:**

| enrollmentNo | formNo | name | fatherName | age | gotra | address | dehri | phone | photoURL |
|---|---|---|---|---|---|---|---|---|---|
| 0420348 | 42 | ईतेन्द्र कृष्ण | राधारमण गौतम | 30 वर्ष लगभग | | गौतम पाड़ा वृन्दावन | करन सिंह गौतम | 9837710234 | |
| 0420001 | 1 | राम प्रसाद शर्मा | श्री कृष्ण दास | 45 वर्ष लगभग | भारद्वाज | लोई बाज़ार वृंदावन | रघुनाथ शर्मा | 9876543210 | |

**photoURL column**: अगर फोटो नहीं है तो खाली छोड़ें।
फोटो के लिए: Google Drive पर upload करें → "Share" → "Anyone with link" → Copy link का यह format:
`https://drive.google.com/uc?id=FILE_ID`

---

## Step 4 — Sheet को Public करें (CSV as URL)

1. **File** → **Share** → **Publish to web**
2. "Link" tab में:
   - पहला dropdown: **Sheet1** चुनें
   - दूसरा dropdown: **Comma-separated values (.csv)** चुनें
3. **"Publish"** दबाएं → **"OK"**
4. जो URL बनेगा उसे **COPY करें**

यह URL कुछ ऐसा दिखेगा:
```
https://docs.google.com/spreadsheets/d/1abc123xyz/pub?gid=0&single=true&output=csv
```

> ⚠️ यह URL SECRET नहीं है — कोई भी डेटा पढ़ सकता है।
> इसलिए phone number के अलावा कोई private जानकारी न डालें।

---
---

# PART 2 — GitHub Pages पर Host करें

## Step 5 — GitHub Account बनाएं

1. **github.com** खोलें
2. "Sign up" → Email, Username, Password भरें
3. Free plan चुनें

---

## Step 6 — Repository बनाएं

1. Login के बाद **"+ New repository"** दबाएं
2. Repository name: `panda-sabha` (याद रखें — URL में आएगा)
3. **Public** रखें ✅
4. **"Add a README file"** ✅ tick करें
5. **"Create repository"** दबाएं

---

## Step 7 — Files Upload करें

1. Repository खुलने के बाद **"Add file"** → **"Upload files"**
2. **`purohit.html`** और **`admin.html`** दोनों drag & drop करें
3. Commit message: `Add purohit QR system`
4. **"Commit changes"** दबाएं

---

## Step 8 — GitHub Pages Enable करें

1. Repository में **"Settings"** tab
2. बाईं तरफ → **"Pages"**
3. Source: **"Deploy from a branch"**
4. Branch: **"main"** → **"/ (root)"** → **Save**
5. 2-3 मिनट रुकें

### आपकी Website का URL बनेगा:
```
https://YOUR_GITHUB_USERNAME.github.io/panda-sabha/
```

जैसे: `https://vrindavanpandasabha.github.io/panda-sabha/`

---

## Step 9 — purohit.html में Sheet URL डालें

1. GitHub पर `purohit.html` खोलें
2. ✏️ (Edit) icon दबाएं
3. यह line खोजें:
   ```javascript
   const SHEET_CSV_URL = "YOUR_GOOGLE_SHEET_CSV_URL_HERE";
   ```
4. Step 4 का copied URL डालें:
   ```javascript
   const SHEET_CSV_URL = "https://docs.google.com/spreadsheets/d/.../pub?gid=0&single=true&output=csv";
   ```
5. **"Commit changes"** → **"Commit directly to the main branch"** → Save

---
---

# PART 3 — Admin Panel Use करें

## Step 10 — Admin Panel खोलें

Browser में जाएं:
```
https://YOUR_USERNAME.github.io/panda-sabha/admin.html
```

**Default Password:** `pandasabha123`

---

## Step 11 — Admin Panel Setup

1. Login करें
2. **Google Sheet CSV URL** field में Step 4 का URL डालें
3. **Purohit Page URL** field में डालें:
   ```
   https://YOUR_USERNAME.github.io/panda-sabha/purohit.html
   ```
4. **"सेटिंग सहेजें"** दबाएं
5. **"शीट लोड करें"** दबाएं → सभी पुरोहित दिखने लगेंगे!

---

## Step 12 — QR Generate करें

1. बाईं सूची में किसी पुरोहित पर क्लिक करें
2. दाईं तरफ QR Code + ID Card Preview दिखेगा
3. **"⬇️ QR PNG डाउनलोड करें"** दबाएं
4. QR image को print करें और पहचान पत्र पर लगाएं

---
---

# नया पुरोहित कैसे जोड़ें?

1. Google Sheet खोलें
2. नई row में data भरें
3. Admin Panel में **"🔄"** (refresh) दबाएं
4. नया पुरोहित list में दिखेगा
5. उसका QR generate करें

**बस इतना!** कोई coding नहीं।

---

# Admin Password कैसे बदलें?

GitHub पर `admin.html` edit करें:

```javascript
// यह line खोजें:
const ADMIN_PASSWORD = "pandasabha123";

// अपना नया password डालें:
const ADMIN_PASSWORD = "आपका_नया_पासवर्ड";
```

---

# QR Code कैसे काम करता है?

```
पहचान पत्र पर QR print है
          ↓
कोई भी QR scan करे (Camera/WhatsApp)
          ↓
Browser खुलता है:
https://username.github.io/panda-sabha/purohit.html?searchID=0420348
          ↓
Page Google Sheet से डेटा लेता है
          ↓
पुरोहित की पूरी जानकारी दिखती है ✅
```

---

# अक्सर पूछे जाने वाले सवाल

**Q: क्या सब free है?**
A: हाँ! GitHub Pages और Google Sheets दोनों बिल्कुल free हैं।

**Q: Data कहाँ save होता है?**
A: Google Sheets में — आप कभी भी edit कर सकते हैं।

**Q: Sheet update करने पर QR बदलता है?**
A: नहीं — QR वही URL point करता है, बस profile page पर नई जानकारी दिखेगी।

**Q: क्या offline काम करेगा?**
A: नहीं — QR scan करने वाले को internet चाहिए होगा।

**Q: Custom domain कैसे लगाएं?**
A: GitHub Pages Settings → Custom domain → अपना domain डालें।
DNS provider पर CNAME record add करें जो `username.github.io` को point करे।

**Q: फोटो upload कहाँ करें?**
A: Google Drive पर upload करें → "Anyone with link can view" → 
URL format: `https://drive.google.com/uc?id=FILEID`
यह URL Sheet के `photoURL` column में डालें।

---

## 📞 मदद चाहिए?

किसी भी step में दिक्कत हो — screenshot लेकर पूछें।
