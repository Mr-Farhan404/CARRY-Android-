# CARRY — Native Android Application (Pure Java)

The official native Android application for **CARRY** (Peer-to-Peer KUET Campus Delivery & Carpooling Platform), engineered with **pure Java**, Google Material3, ViewBinding, Retrofit 2, and Firebase Cloud Services.

---

## 📱 Features & Highlights

1. **Campus Shop & Catalog**:
   - Live product browsing across categories (**🍔 Food & Snacks**, **🔌 Electronics**, **📚 Stationery & Others**).
   - Real-time search by keyword and category filters.
   - Quantity adjustment selector directly on product cards (`- [qty] +`).
   - **🛒 Add to Cart** for multi-item batch ordering.
   - **⚡ Express Order Now**: Isolated checkout dialog for immediate single-product orders.

2. **Upfront MFS Payment Portal (bKash / Nagad)**:
   - Integrated into Express Order Now, Cart Bottom Sheet, and Custom Request screens.
   - Automatic live calculation: `Product Cost + Base Delivery Fee + MFS Fee = Total to Send`.
   - Brand-matched bKash (Pink) and Nagad (Orange) selectors with account copy button.
   - Sender Phone Number and TrxID validation.

3. **Multi-Item Shopping Cart**:
   - Header badge displaying real-time item count.
   - Interactive Bottom Sheet showing item list with live +/- quantity adjustments and item deletion.
   - Single-tap batch checkout for multiple campus items.

4. **Custom Manual Requests**:
   - Post any item needed from Khulna city to KUET.
   - Specify Item Name, Category, Quantity, Budget, Khulna Pickup Zone (New Market, Sonadanga, etc.), and special instructions.

5. **Order Tracking & Lifecycle Management**:
   - Status flow: `REQUESTED` -> `ACCEPTED` -> `COLLECTED` -> `RETURNING` -> `READY_FOR_DELIVERY` -> `DELIVERED` -> `CANCELLED`.
   - Detailed step-by-step timeline of delivery progression with timestamps and notes.
   - Need-More Additional Payment Support: City carriers can request extra funds if store pricing differs.

6. **Carrier / Delivery Hub (Earn Delivery Money)**:
   - Post a trip when heading from KUET to Khulna city (destination, departure, capacity).
   - Advance trip status (`In City` -> `Returning` -> `Done`).
   - Browse open campus requests and accept them to earn delivery charges.
   - **Live GPS Sharing**: Share real-time coordinates so waiting students can track delivery on Google Maps.

7. **Real-Time Order Chat (Firebase Firestore)**:
   - Order-scoped 1-to-1 live messaging between customer and assigned delivery partner.
   - Offline detection banner informing when the counterpart has not joined the room yet.
   - Clean message lifecycle attached in `onStart` and detached in `onStop` to preserve battery.

8. **KUET Student Profile & Multi-Role Administration**:
   - Student ID, Department, Contact info, and Verified KUET badge.
   - Roles: Student, Delivery Partner, Moderator, and Full Administrator.
   - In-app application forms for Delivery Partner and Moderator accreditation.
   - Full Admin Operations: User account management (promote/delete), catalog management (add/edit products), and campus order audits.
   - **Backend Environment Switcher**:
     - `Local Emulator` (`http://10.0.2.2:8080/`)
     - `Cloud Backend` (`https://carry-backend-hctl.onrender.com/`)

---

## 🛠️ Technology Stack

- **Language:** Pure Java (100% Kotlin-free, minSdk 24, targetSdk 34)
- **UI Framework:** Android Jetpack, ViewBinding, Material Design 3
- **Networking:** Retrofit 2, OkHttp 3, Gson
- **Firebase Platform:**
  - Firebase Authentication (mirrored student accounts)
  - Cloud Firestore (user profiles, base64 photo storage, order chat)
  - Realtime Database (live status events, partner GPS tracking)
  - Firebase Security Rules (production-hardened rules)
- **Architecture:** MVVM (Model-View-ViewModel) + Repository / Store Pattern
- **Testing:** JUnit 4, Robolectric, Mockito

---

## 🚀 How to Open and Run in Android Studio

1. **Launch Android Studio**.
2. Click **Open** (or **File -> Open...**).
3. Select this project root folder.
4. Click **OK** to sync Gradle dependencies.
5. Select an Android Virtual Device (e.g. Pixel running API 34).
6. Click **Run (▶)** (or press `Shift + F10`).

---

## 🧪 Running Unit Tests

```bash
./gradlew testDebugUnitTest
```

All 7 test suites (AuthCoordinatorTest, ChatViewModelTest, LiveStatusTest, ProfileViewModelTest, ImageResizerTest) run hermetically.

---

## 🔑 Demo Account Credentials

- **Email:** `farhan@kuet.ac.bd`
- **Password:** `password123`
- *Or register a new student account using your KUET student email.*

---

## 📁 Repository Structure

```
├── app/
│   ├── src/main/
│   │   ├── AndroidManifest.xml
│   │   ├── java/com/carry/app/
│   │   │   ├── MainActivity.java
│   │   │   ├── adapters/
│   │   │   ├── api/
│   │   │   ├── data/firebase/      # Firebase store implementations
│   │   │   ├── models/             # Domain and DTO models
│   │   │   ├── ui/                 # Activities, Fragments, ViewModels
│   │   │   └── utils/              # Resizer, SessionManager, Formatters
│   │   └── res/
│   └── src/test/                   # Unit test suites
├── firebase-rules/                 # Firestore, RTDB, and Storage security rules
├── docs/                           # Integration documentation
├── CARRY_Android_Project_Report.docx # Comprehensive project report
├── build.gradle
├── settings.gradle
└── gradle.properties
```
