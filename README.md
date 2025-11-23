# Secure Notes 🔒📝

> **Your private digital sanctuary.**

Secure Notes is a privacy-first, end-to-end encrypted note-taking application designed with a premium, native iOS-style interface. It ensures that your thoughts remain exclusively yours through client-side encryption and a strict zero-knowledge architecture.

---

## ✨ Key Features

### 🔒 Security & Privacy (Core)
* **End-to-End Encryption:** Uses **AES-256-GCM** to encrypt note titles and content before they ever leave your device.
* **Client-Side Key Derivation:** Utilizes **PBKDF2** with 310,000 iterations to derive strong encryption keys from your password locally.
* **Zero-Knowledge Architecture:** The server (Firebase) only stores encrypted blobs—never your password or plaintext notes.
* **Vault Locking:** Instantly clear decrypted data from memory with a dedicated "Lock Vault" button.

### 📝 Note Management
* **Rich Editor:** Clean, distraction-free writing experience.
* **Pinning:** Keep important notes pinned to the top of your list.
* **Smart Search:** Real-time search filtering through decrypted titles and content.
* **Trash / Recently Deleted:** Soft delete mechanism with options to restore or permanently delete.
* **Live Statistics:** Real-time word and character count displayed in the editor toolbar.
* **Quick Copy:** One-tap button to copy note text to the clipboard.

### 🎨 Premium iOS-Style UI/UX
* **Sidebar Navigation:** Native-style slide-out menu for switching between All Notes and Trash.
* **Dark Mode:** Fully adaptive Dark Mode that toggles via Settings or matches system preferences.
* **Action Sheets:** Premium slide-up menus for destructive actions (Delete, Empty Trash) with blur effects.
* **Smart Date Formatting:** Relative time formatting (e.g., "10:42 AM", "Yesterday", "5/23/24").
* **Smooth Transitions:** 60fps hardware-accelerated slide animations.
* **Haptic Feedback:** Visual "touch down" states on buttons.

### 💾 Data Management
* **Encrypted Backup:** Export your entire vault (metadata included) to a local `.json` file.
* **Restore Vault:** Import a backup file to restore data (requires the specific password used for that backup).
* **Cloud Sync:** Real-time synchronization across devices using Firebase Firestore.

---

## ⚙️ Tech Stack

* **Frontend:** HTML5, Tailwind CSS (via CDN), Vanilla JavaScript (ES6 Modules).
* **Backend:** Firebase Authentication & Firestore.
* **Cryptography:** Native Web Crypto API (`SubtleCrypto`).
* **Icons:** FontAwesome 6.

---

## 🚀 Getting Started — Firebase Setup

To run this application securely, you must link it to your own Firebase project.

### 1. Create the Project
1.  Go to the [Firebase Console](https://console.firebase.google.com/).
2.  Click "Add project" and name it (e.g., `SecureNotesVault`).
3.  Disable Google Analytics (not required).
4.  Click **Create Project**.

### 2. Enable Authentication
1.  Go to **Build > Authentication**.
2.  Click **Get Started**.
3.  Select **Email/Password** provider.
4.  Enable it and click **Save**.

### 3. Create the Database
1.  Go to **Build > Firestore Database**.
2.  Click **Create Database**.
3.  Select a location (e.g., `us-central1`).
4.  Select **Start in production mode**.

### 4. Set Security Rules (Critical)
Go to the **Rules** tab in Firestore and paste this code to ensure users can only access their own data:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

### 5. Connect the App

1. Go to **Project Settings** (Gear icon).
2. Scroll to "Your apps" and click the **Web (</>)** icon.
3. Register the app (e.g., "SecureNotes Web").
4. Copy the `firebaseConfig` object provided.
5. Open `index.html` (or your config file) in this repository.
6. Replace the placeholder config with your actual API keys:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.firebasestorage.app",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

### 🛡️ Security Notice

**⚠️ IMPORTANT:** This application performs all encryption in the browser.
* **If you lose your Master Password, your data is mathematically lost forever.**
* There is no "Forgot Password" feature because the server never receives (and therefore cannot verify or reset) your password.
* Always keep a backup of your data.

### 📄 License

This project is licensed under the **MIT License**. You are free to use, modify, and distribute this software.
