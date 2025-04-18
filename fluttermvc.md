
# Flutter MVC Architecture with Provider – Best Practices & Boilerplate

---

## 📚 Explanation by Uma Palve

### ✅ Structure Per Module
Each module contains 4 files:

1. **UI (View)** – Flutter widgets & user interface.
2. **Controller** – Handles logic (no API calls).
3. **Provider** – Responsible only for API calls (no logic).
4. **Model** – JSON to object conversion.

---

### 🔁 API Call Flow
1. Common API call (GET, POST, PUT, DELETE) is made using `api_service.dart`.
2. This response is passed to the **Provider**.
3. Provider converts the response (JSON) into **Model** object.
4. Provider sends the model to the **Controller**.
5. Controller handles logic and updates the **View**.

---

## ✅ Why This is a Good Practice?
This MVC structure is:
- ✅ Clean and modular
- ✅ Testable and maintainable
- ✅ Scalable for large teams or projects
- ✅ Easy for onboarding developers

### 🔧 Suggestions to Enhance
- Use `ChangeNotifier` or `Riverpod` for reactive state updates.
- Add centralized error handling.
- Implement logging.
- Consider Dependency Injection using `get_it`.

---

## 📁 Flutter Project Folder Structure

```
lib/
├── modules/
│   └── login/
│       ├── login_view.dart          👈 UI (View)
│       ├── login_controller.dart    👈 Logic (Controller)
│       ├── login_provider.dart      👈 API Integration
│       └── login_model.dart         👈 Model (JSON Object)
├── network/
│   └── api_service.dart             👈 Common API methods (GET, POST, PUT, DELETE)
```

---

## 🧩 Sample Boilerplate Code

### 🔹 main.dart

```dart
import 'package:flutter/material.dart';
import 'modules/login/login_view.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter MVC Template',
      theme: ThemeData(primarySwatch: Colors.blue),
      home: LoginView(),
    );
  }
}
```

---

### 🔹 network/api_service.dart

```dart
import 'dart:convert';
import 'package:http/http.dart' as http;

class ApiService {
  final String baseUrl = 'https://yourapi.com/api';

  Future<dynamic> post(String endpoint, Map<String, dynamic> body) async {
    final response = await http.post(
      Uri.parse('$baseUrl$endpoint'),
      headers: {'Content-Type': 'application/json'},
      body: jsonEncode(body),
    );

    if (response.statusCode == 200) {
      return jsonDecode(response.body);
    } else {
      print('Error: ${response.body}');
      return null;
    }
  }
}
```

---

### 🔹 modules/login/login_model.dart

```dart
class LoginResponse {
  final bool success;
  final String message;

  LoginResponse({required this.success, required this.message});

  factory LoginResponse.fromJson(Map<String, dynamic> json) {
    return LoginResponse(
      success: json['success'] ?? false,
      message: json['message'] ?? '',
    );
  }
}
```

---

### 🔹 modules/login/login_provider.dart

```dart
import '../../network/api_service.dart';
import 'login_model.dart';

class LoginProvider {
  final ApiService _api = ApiService();

  Future<LoginResponse?> login(String username, String password) async {
    final response = await _api.post('/login', {
      'username': username,
      'password': password,
    });

    if (response != null) {
      return LoginResponse.fromJson(response);
    }
    return null;
  }
}
```

---

### 🔹 modules/login/login_controller.dart

```dart
import 'login_provider.dart';
import 'login_model.dart';

class LoginController {
  final LoginProvider _provider = LoginProvider();

  Future<String?> loginUser(String username, String password) async {
    final result = await _provider.login(username, password);

    if (result != null && result.success) {
      return null;
    }
    return result?.message ?? 'Unknown error';
  }
}
```

---

### 🔹 modules/login/login_view.dart

```dart
import 'package:flutter/material.dart';
import 'login_controller.dart';

class LoginView extends StatefulWidget {
  @override
  _LoginViewState createState() => _LoginViewState();
}

class _LoginViewState extends State<LoginView> {
  final _usernameController = TextEditingController();
  final _passwordController = TextEditingController();
  final _controller = LoginController();
  String? _errorMessage;

  void _login() async {
    final username = _usernameController.text;
    final password = _passwordController.text;
    final result = await _controller.loginUser(username, password);

    setState(() {
      _errorMessage = result;
    });

    if (result == null) {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text('Login Successful')),
      );
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Login')),
      body: Padding(
        padding: const EdgeInsets.all(20.0),
        child: Column(
          children: [
            TextField(
              controller: _usernameController,
              decoration: InputDecoration(labelText: 'Username'),
            ),
            TextField(
              controller: _passwordController,
              decoration: InputDecoration(labelText: 'Password'),
              obscureText: true,
            ),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: _login,
              child: Text('Login'),
            ),
            if (_errorMessage != null)
              Padding(
                padding: const EdgeInsets.only(top: 10),
                child: Text(
                  _errorMessage!,
                  style: TextStyle(color: Colors.red),
                ),
              ),
          ],
        ),
      ),
    );
  }
}
```

---

## ✅ Summary

This architecture:
- Keeps your Flutter app **modular**
- Follows the **MVC pattern**
- Uses `Provider` only for **API communication**
- Is easy to **test, scale, and maintain**

Ready to expand with more modules like `Register`, `Profile`, etc.
