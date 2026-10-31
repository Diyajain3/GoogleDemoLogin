# 🔑 Learn Google Login (White & Violet Edition)

An educational, interactive React application designed to teach **Google Identity Services (GIS)**, **OAuth 2.0**, and **OpenID Connect (OIDC)** authentication with a modern **White & Violet** Tailwind CSS user interface.

---

## 🎨 Theme & Design
- **Primary Color Scheme**: Pure White & Rich Violet (`#7c3aed`, `#6d28d9`, violet-50 to violet-900).
- **Styling**: Tailwind CSS v4 with Vite integration.
- **Icons**: Lucide React.
- **Features**: Frosted cards, ambient violet glows, responsive layouts, and interactive token inspector tabs.

---

## 📦 Installed Packages & Why They Are Needed

| Package | Purpose |
| :--- | :--- |
| **`tailwindcss` & `@tailwindcss/vite`** | Modern styling framework providing the clean White & Violet design system without external CSS files. |
| **`react-router-dom`** | Client-side routing between `/login` and the protected `/` dashboard. |
| **`jwt-decode`** | Decodes the cryptographically signed Google ID Token (JWT) into user claims (name, email, avatar, sub). |
| **`lucide-react`** | High-quality icons for status indicators, tokens, security badges, and buttons. |

---

## 🎓 How Google Login Works (The Learning Flow)

```
+-------------------------------------------------------------------+
| 1. App initializes Google Identity Services script (gsi/client)    |
|    with your OAuth 2.0 Client ID.                                 |
+---------------------------------+---------------------------------+
                                  |
                                  v
+---------------------------------+---------------------------------+
| 2. User clicks "Continue with Google" -> Secure Google consent dialog |
+---------------------------------+---------------------------------+
                                  |
                                  v
+---------------------------------+---------------------------------+
| 3. Google authenticates the user and returns a signed ID Token     |
|    (JWT) to the callback: `handleCredentialLogin(response)`.      |
+---------------------------------+---------------------------------+
                                  |
                                  v
+---------------------------------+---------------------------------+
| 4. Frontend uses `jwtDecode(credential)` to read user claims:     |
|    - `name`, `email`, `picture`, `sub` (unique permanent ID)       |
+---------------------------------+---------------------------------+
                                  |
                                  v
+---------------------------------+---------------------------------+
| 5. Token & profile stored in `localStorage` -> `<ProtectedRoute>` |
|    unlocks access to the Dashboard!                               |
+-------------------------------------------------------------------+
```

---

## ⚙️ Google Cloud Console Configuration

To use your real Google account with this project:

1. Go to the [Google Cloud Console Credentials Page](https://console.cloud.google.com/apis/credentials).
2. Click **Create Credentials** -> **OAuth client ID**.
3. Application type: **Web application**.
4. In **Authorized JavaScript origins**, add:
   - `http://localhost:5173`
   - `http://localhost`
5. Copy your **Client ID** and add it to your `.env` file:
   ```env
   VITE_GOOGLE_CLIENT_ID="your-client-id.apps.googleusercontent.com"
   ```
6. Start the development server:
   ```bash
   npm run dev
   ```

> 💡 **Instant Simulation / Demo Mode**:
> If you haven't set up your Google Cloud origins yet, click the **"Launch Demo Login"** button on the login screen to simulate the entire login flow, inspect decoded claims, and test protected routes instantly!

---

## 🛡️ Production Note: Frontend vs Backend Security
- **Frontend Token Decoding**: Good for immediately personalizing the UI (avatar, name).
- **Backend Token Verification**: Never trust decoded tokens on your backend without verifying Google's cryptographic signature using `google-auth-library` (`verifyIdToken`).

---

## 🚀 Scripts
- `npm run dev` - Launch local Vite dev server
- `npm run build` - Compile production bundle with Tailwind CSS
