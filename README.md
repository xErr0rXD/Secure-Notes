# Secure Notes 🔒📝  
**Your private digital sanctuary.**  

SecureNotes is a privacy-first, end-to-end encrypted note-taking application designed with a premium iOS-style interface. It ensures that your thoughts remain exclusively yours through client-side encryption and a zero-knowledge architecture.

## ✨ Key Features  

### 🔒 Security & Privacy (Core)
- **End-to-End Encryption:** Uses **AES-256-GCM** to encrypt both note titles and content before they leave your device.
- **Client-Side Key Derivation:** Utilizes **PBKDF2** with 310,000 iterations to derive robust encryption keys from your password locally.
- **Zero-Knowledge Architecture:** The server (Firebase) only stores encrypted blobs. It never sees your password or raw note data.
- **Vault Locking:** Manually lock the vault via Settings to instantly clear decrypted data from memory.

### 📝 Note Management
- **Rich Editor:** Clean, distraction-free writing experience.
- **Pinning:** Keep important notes at the top.
- **Smart Search:** Real-time filtering through titles and decrypted content.
- **Trash / Recently Deleted:**
  - Soft-delete mechanism for safety.
  - **Recover** notes from Trash.
  - **Permanent Delete** to wipe forever.
- **Live Statistics:** Real-time word and character counts in the editor toolbar.
- **Quick Copy:** One-tap copy to clipboard.

### 🎨 Premium iOS-Style UI/UX
- **Sidebar Navigation:** Smooth slide-out sidebar for All Notes and Trash.
- **Dark Mode:** Fully adaptive or system-following.
- **Action Sheets:** iOS-style slide-up menus with blur effects for destructive actions.
- **Smart Date Formatting:**  
  - Today → shows time (e.g., “10:42 AM”)  
  - Yesterday → shows “Yesterday”  
  - Older → shows full date (e.g., “5/23/24”)  
- **Smooth Transitions:** 60fps hardware-accelerated page animations.
- **Haptic Feedback:** Native-like touch states on buttons.

### 💾 Data Management
- **Encrypted Backup:** Export your entire encrypted vault into a `.json` file.
- **Restore Vault:** Import backup files (requires the same password used to create them).
- **Cloud Sync:** Seamless real-time sync using Firebase Firestore.


## ⚙️ Tech Stack
- **Frontend:** HTML5, Tailwind CSS, Vanilla JavaScript (ES6 Modules)
- **Backend:** Firebase Authentication & Firestore
- **Cryptography:** Web Crypto API (SubtleCrypto)
- **Icons:** FontAwesome 6

## 🛡️ Security Notice
SecureNotes performs all encryption **in your browser**.  
We never store your Master Password.  
If you lose it, your data is mathematically unrecoverable—there is **no password reset**.

## 📄 License
This project is licensed under the **MIT License**.
