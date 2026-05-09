# Student Portal

A web-based student information portal with Firebase backend for data persistence.

## Features
- Student data search and update
- Seat reference guide
- Admin panel for data management
- Firebase cloud database integration
- Excel import/export functionality

## Setup Instructions

### 1. Firebase Setup
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create a new project
3. Enable Firestore Database
4. Go to Project Settings > General > Your apps
5. Add a web app and copy the Firebase config
6. Replace the config in `index.html` with your actual values

### 2. Firebase Config
✅ **Already configured** with your Firebase project settings. No changes needed.

Your Firebase project: `hostel-data-update`

### 3. Deploy to GitHub Pages
1. Push this code to a GitHub repository
2. Go to repository Settings > Pages
3. Select "Deploy from a branch" and choose main/master
4. The site will be live at: `https://yourusername.github.io/repository-name`

### 4. Initial Data Setup
- Use the Admin panel to import student data from Excel
- Or manually add students through the interface
- All data is automatically saved to Firebase

## Security Rules

### Firestore Security Rules (IMPORTANT!)
Your current rules allow anyone to read/write data. **This is dangerous!**

**Replace your current rules with this secure version:**

``
```

**🔧 TEMPORARY TESTING RULES (Use this first to test if Firebase works):**

⚠️ **Use the testing rules temporarily, then switch to secure ones after confirming Firebase works**

**To update rules:**
1. Go to Firebase Console → Firestore Database → Rules
2. Replace the existing code with the secure rules above
3. Click "Publish"

### Testing Security:
After updating rules, test them:
1. Open your website
2. Open browser console (F12)
3. Run: `testFirebaseSecurity()`
4. Should show: "✅ Security working: Invalid write blocked"

### Option 2: Maximum Security (Requires Authentication)

If you want full security, enable Firebase Authentication:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /students/{studentId} {
      // Only authenticated users can read/write
      allow read, write: if request.auth != null;
    }
  }
}
```

**But this requires:**
- Adding Firebase Auth to your website
- Students need to create accounts
- More complex user experience

---

### Current Risk Assessment:
- **High Risk**: Public read/write allows data theft
- **Medium Risk**: Current rules allow viewing all data
- **Low Risk**: Secure rules prevent unauthorized changes

**Recommendation**: Use the secure rules I provided above. They balance security with usability.

## Files
- `index.html` - Main application
- `1.jpg` - Seat reference image
- `.gitignore` - Excludes sensitive files