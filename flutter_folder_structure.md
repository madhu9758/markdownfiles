
# 📁 Flutter Project Folder Structure

```
lib/
├── main.dart                 👈 Entry point of the app
├── app_binding.dart         👈 App-wide dependency bindings
├── app/
│   ├── modules/
│   │   └── login/
│   │       ├── login_view.dart          👈 UI (View)
│   │       ├── login_controller.dart    👈 Logic (Controller)
│   │       ├── login_provider.dart      👈 API Integration
│   │       └── login_model.dart         👈 Model (JSON Object)
│   └── network/
│       └── api_service.dart             👈 Common API methods (GET, POST, PUT, DELETE)
```
