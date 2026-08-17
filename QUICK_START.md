# Quick Start Guide - MeetMedia

## ⚡ 5 Minutes Setup

### Step 1: Get Firebase Credentials (2 min)
1. Go to https://console.firebase.google.com
2. Click "Add Project" → Name it "MeetMedia" → Create
3. Once created, go to Project Settings (⚙️ icon)
4. Under "Your apps", click the </> icon to create a web app
5. Copy the config object shown

### Step 2: Update config.js (1 min)
1. Open `config.js` in the MeetMedia folder
2. Find this section:
```javascript
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    // ... other fields
};
```
3. Replace YOUR_API_KEY, YOUR_PROJECT_ID, etc. with your copied values
4. Save the file

### Step 3: Enable Firebase Features (1 min)

**Enable Authentication:**
- In Firebase Console → Authentication → Get Started
- Click "Email/Password" → Enable it
- Click "Google" → Enable it with a support email → Save

**Create Firestore:**
- Firebase Console → Firestore Database → Create Database
- Choose "Production Mode" → Select your region → Create

### Step 4: Run Locally (1 min)

**On Windows (PowerShell):**
```powershell
python -m http.server 8000
```
Then open http://localhost:8000

OR

**Using Node.js:**
```bash
npx http-server
```

### Step 5: Test It Out! ✅

1. Open http://localhost:8000
2. Click "Get Started Free"
3. Create a new account
4. Explore the dashboard!

---

## 📁 File Guide

| File | Purpose |
|------|---------|
| **index.html** | Landing page - First page users see |
| **signup.html** | Registration page - Create new account |
| **login.html** | Login page - Sign in to account |
| **dashboard.html** | Main app - After login |
| **config.js** | Firebase settings (UPDATE THIS!) |
| **README.md** | Full documentation |
| **FIREBASE_SETUP.md** | Detailed Firebase guide |

---

## 🔑 Key Features

✅ **Email/Password Login**
- Users can create account with email
- Passwords are secured by Firebase

✅ **Google Sign-In**
- One-click login with Google account
- No password needed

✅ **Dashboard with Tabs:**
- 🏠 **Home** - Welcome & stats
- 🔍 **Discover** - Find people to connect
- 💬 **Messages** - Chat conversations
- 📅 **Events** - Local events
- 👤 **Profile** - Your information
- ⚙️ **Settings** - Preferences

---

## 🔗 Important Links

- **Firebase Console:** https://console.firebase.google.com
- **Firebase Docs:** https://firebase.google.com/docs
- **For Help:** Check FIREBASE_SETUP.md or README.md

---

## ⚠️ Common Issues & Fixes

**"Firebase is not defined" error:**
- Make sure config.js loads after Firebase scripts in the HTML ✓ Already done

**Google Sign-In not working:**
- Go to Firebase Authentication → Google provider
- Add your domain to "Authorized Domains"

**Can't create account:**
- Email must be valid format (example@gmail.com)
- Password must be 6+ characters
- Check browser console (F12) for error details

---

## 🚀 Next: Deploy Your App

### Deploy to Firebase Hosting (Easiest):
```bash
npm install -g firebase-tools
firebase login
firebase init hosting
firebase deploy
```

### Or use Netlify:
1. Go to https://netlify.com
2. Drag and drop the MeetMedia folder
3. Done! Your app is live

### Or use Vercel:
1. Go to https://vercel.com
2. Import your GitHub repo
3. Click Deploy

---

## 📊 Project Structure

```
MeetMedia/
├── index.html              ← Public landing page
├── signup.html             ← Registration
├── login.html              ← Login
├── dashboard.html          ← Main app
├── config.js               ← Firebase config ⭐ UPDATE THIS
├── README.md               ← Full docs
├── FIREBASE_SETUP.md       ← Firebase guide
├── QUICK_START.md          ← This file
└── SETUP_SUMMARY.txt       ← Setup overview
```

---

## 💡 Tips

1. **Test User**: Create a test account first to verify everything works
2. **Chrome DevTools**: Press F12 to see console errors
3. **Responsive**: Test on mobile using Chrome DevTools (Ctrl+Shift+M)
4. **Customization**: Edit colors in the CSS `<style>` sections
5. **Database**: Check Firestore in Firebase Console to see stored data

---

## What to Customize

1. **Colors**: Search for `#667eea` in CSS to change purple
2. **Text**: Update company name "MeetMedia" to your name
3. **Logo**: Replace emoji 🎯 with your logo
4. **Features**: Add more tabs to dashboard in dashboard.html
5. **Data**: Add more fields to user profiles in Firestore

---

Happy Coding! 🎉

Questions? Check the docs folder or Firebase Documentation.
