# SmartTrash

SmartTrash is a comprehensive Flutter application for intelligent waste management, designed for visualization, analysis, and optimization of urban waste collection. It integrates advanced features for real-time monitoring, data analysis, report generation, notifications, and AI-based recommendations.

---

## Main Features

### 1. **Dynamic Dashboard**
- **Overview** of trash bin fill levels, gas, temperature, humidity, etc.
- **Interactive charts** (Syncfusion, fl_chart) to visualize trends, correlations, and distributions.
- **Key indicators**: number of full bins, trucks needed, required employees, etc.

### 2. **Advanced Analysis**
- **Population analysis**: correlation between trash bin usage and population by area.
- **Environmental analysis**: monitoring of gas levels, temperature, humidity, and environmental alerts.
- **Pattern analysis**: display of dynamic Markdown reports generated server-side (NLP, trends, etc.).
- **Anomaly recommendations**: automatic action suggestions when anomalies are detected (AI).

### 3. **Report Generation and Visualization**
- **On-demand PDF report generation**, downloadable on mobile and web.
- **Integrated visualization** of PDF reports (mobile/desktop).

### 4. **Notifications**
- **Push notifications** via Firebase Cloud Messaging for important alerts (full bins, high gas levels, etc.).

### 5. **User Management**
- **Authentication** (Firebase Auth).
- **Role management** (admin/user) for access to advanced features.

### 6. **Settings**
- **Dynamic configuration** of backend server URL via the interface.
- **User preference saving** (SharedPreferences).

---

## Technical Architecture

- **Flutter** (cross-platform: Web, Android, iOS, Desktop)
- **Backend**: REST API (e.g., FastAPI, Flask) for data aggregation and analysis
- **Firebase**: Auth, Realtime Database, Cloud Messaging
- **Syncfusion** & **fl_chart**: advanced data visualization
- **Permission management**: storage access, notifications, etc.

---

## Main Screen Structure

- `home_screen.dart`: Home page, main navigation
- `waste_dashboard.dart`: Dashboard and visualizations
- `final_rapport_generation_screen.dart`: PDF report generation and display
- `analyse_population_tab.dart`: Population analysis and correlations
- `anomaly_recommendation_screen.dart`: AI recommendations for anomalies
- `patterns_analysis_viewer_screen.dart`: Dynamic display of Markdown analyses
- `app_settings.dart`: Settings management and server URL

---

## Installation & Launch

1. **Clone the repository**
2. **Configure Firebase**

   To connect SmartTrash to Firebase:

   1. **Create a Firebase project**  
      Go to [https://console.firebase.google.com/](https://console.firebase.google.com/), create a project and follow the instructions.

   2. **Add an application to your project**  
      - For web: add a web application and retrieve the configuration (`apiKey`, `authDomain`, etc.).
      - For Android/iOS: add the corresponding applications and follow the instructions for `google-services.json` (Android) or `GoogleService-Info.plist` (iOS) files.

   3. **Configure files in the Flutter project**  
      - **Web**:  
        - Place the configuration in `web/firebase-config.js`.
      - **Mobile**:  
        - Place `google-services.json` in `android/app/` and/or `GoogleService-Info.plist` in `ios/Runner/`.

   4. **Enable necessary services**  
      - Enable authentication (Email/Password, etc.) in the Firebase console.
      - Enable real-time database or Firestore according to your needs.
      - Enable Cloud Messaging for push notifications.

   5. **Verify integration**  
      - Launch the application. If everything is properly configured, the Firebase connection will be established automatically.

   > **Tip**:  
   > Example configuration files are already present (`firebase_options_web.dart`, `firebase-config.js`).  
   > Adapt them with your own Firebase project keys and identifiers.

3. **Configure the server URL** in the application settings
4. **Install dependencies**
   ```sh
   flutter pub get
   ```
5. **Launch the application**
   ```sh
   flutter run -d chrome   # or android/ios
   ```

---

## Notes

- The application requires a compatible backend (REST API) to function fully.
- Push notifications require Firebase Cloud Messaging configuration.
- PDF reports are generated server-side and retrieved via the API.


---

## Useful Links

- [Flutter Documentation](https://docs.flutter.dev/)
- [Official Syncfusion Flutter Repository](https://github.com/syncfusion/flutter-widgets)
- [Syncfusion Charts Documentation](https://help.syncfusion.com/flutter/chart/overview)
- [Firebase for Flutter Documentation](https://firebase.flutter.dev/docs/overview)
- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [Flask Documentation](https://flask.palletsprojects.com/)

---

**SmartTrash**: Optimize urban waste management through data and artificial intelligence!

---