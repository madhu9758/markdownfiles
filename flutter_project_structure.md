# 📁 Flutter Project Folder Structure


```
lib/
├── main.dart                        👈 Entry point of the app
├── app_binding.dart                👈 App-wide dependency bindings
├── app/
│   ├── modules/
│   │   ├── login/
│   │   │   ├── login_view.dart         👈 UI (View)
│   │   │   ├── login_controller.dart   👈 Logic (Controller)
│   │   │   ├── login_provider.dart     👈 API Integration
│   │   │   └── login_model.dart        👈 Model (JSON Object)
│   │   ├── auth/                       👈 Authentication module
│   │   │   ├── controllers/
│   │   │   │   ├── auth_controller.dart        👈 Auth logic
│   │   │   │   └── login_api_provider.dart     👈 Login API integration
│   │   │   ├── models/
│   │   │   │   └── auth_model.dart             👈 Auth model
│   │   │   └── screen/
│   │   │       ├── auth_screen.dart            👈 Auth UI
│   │   │       └── contact_screen.dart         👈 Contact UI
│   │   ├── dashboard/
│   │   │   └── dashboard_screen.dart           👈 Dashboard UI
│   │   ├── deactive_site/
│   │   │   ├── controller/
│   │   │   │   ├── deactive_site_controller.dart 👈 Controller logic
│   │   │   │   ├── site_model.dart               👈 Site model
│   │   │   │   └── site_provider.dart            👈 API provider
│   │   │   ├── screen/
│   │   │   │   └── deactive_site_screen.dart     👈 Screen UI
│   │   │   └── site_card.dart                    👈 Site card widget
│   │   ├── drawer/
│   │   │   └── drawer_screen.dart                👈 Drawer UI
│   │   ├── face_register/
│   │   │   ├── controller/
│   │   │   │   ├── face_reg_controller.dart     👈 Face registration logic
│   │   │   │   ├── face_reg_model.dart          👈 Face registration model
│   │   │   │   └── face_reg_provider.dart       👈 Face registration API
│   │   │   ├── widget/
│   │   │   │   ├── face_register_camera.dart     👈 Camera widget for face register
│   │   │   │   ├── face_register_card.dart       👈 Card widget for face register
│   │   │   │   └── face_register_popup.dart      👈 Popup widget for face register
│   │   │   └── face_register_screen.dart         👈 Face register screen
│   │   ├── gaurd/
│   │   │   ├── controller/
│   │   │   │   ├── guard_api.dart                👈 Guard API logic
│   │   │   │   └── guard_controller.dart         👈 Guard controller logic
│   │   │   ├── model/
│   │   │   │   └── get_guard_list_model.dart     👈 Guard list model
│   │   │   ├── widget/
│   │   │   │   └── assign_gaurd_popup.dart       👈 Popup to assign guard
│   │   │   └── view_assign_gaurd.dart            👈 UI to view assigned guard
│   │   ├── home/
│   │   │   ├── controller/
│   │   │   │   ├── upcoming_controller.dart      👈 Upcoming logic
│   │   │   │   └── upcoming_provider.dart        👈 Upcoming API
│   │   │   ├── model/
│   │   │   │   └── upcoming_model.dart           👈 Upcoming data model
│   │   │   ├── widget/
│   │   │   │   ├── announcement_card.dart        👈 Announcement card widget
│   │   │   │   ├── ongoing_patrol_summary_card.dart 👈 Ongoing patrol summary
│   │   │   │   ├── shift_or_site_view_card.dart  👈 Shift or Site card
│   │   │   │   └── upcoming_patrol_summary_card.dart 👈 Upcoming patrol summary
│   │   │   └── home_screen.dart                  👈 Home screen UI
│   │   ├── notification/
│   │   ├── patrol/
│   │   ├── policy_document/
│   │   ├── profile/
│   │   ├── qr/
│   │   ├── report_menu/
│   │   ├── site_inspection/
│   │   ├── sos/
│   │   └── splash/
│   ├── network/
│   │   └── api_service.dart                    👈 Common API methods (GET, POST, PUT, DELETE)
│   ├── store/                                   👈 App-wide state management
│   │   ├── api_response.dart                    👈 API response handler
│   │   ├── app_exception.dart                   👈 API exception definitions
│   │   ├── http_client.dart                     👈 HTTP client wrapper
│   │   ├── permission_controller.dart           👈 Permission handling logic
│   │   └── rest_api.dart                        👈 REST API abstraction
│   └── utils/
│       ├── difference_colors.dart               👈 App-specific color definitions
│       ├── difference_text_style.dart           👈 Custom text styles
│       ├── local_notification_service.dart      👈 Local notification utilities
│       ├── shared_preference.dart               👈 Shared Preferences helper
│       ├── notification_listen_helper.dart      👈 Handles foreground/background notification logic
│       ├── helpers/
│       │   ├── app_images.dart                  👈 Image asset paths
│       │   ├── app_language.dart                👈 Language/localization utility
│       │   ├── common_message.dart              👈 Common message constants
│       │   ├── dailog_helper.dart               👈 Custom dialog utilities
│       │   ├── date_formate.dart                👈 Date formatting helper
│       │   ├── decorations.dart                 👈 Box decorations and styles
│       │   ├── flutter_navigation.dart          👈 Navigation helper
│       │   ├── globals.dart                     👈 Global variables/constants
│       │   └── pdf_api.dart                     👈 PDF generation utilities
│       └── widgets/
│           ├── common_app_bar.dart              👈 Common AppBar widget
│           ├── custom_checkbox_widget.dart      👈 Custom checkbox UI
│           ├── dashboard_appbar.dart            👈 Dashboard-specific AppBar
│           ├── employee_dropdown_widget.dart    👈 Dropdown for employee selection
│           ├── empty_state_widget.dart          👈 UI for empty data
│           ├── function_popup.dart              👈 Popup widget for functions
│           ├── pdf_view.dart                    👈 PDF viewer
│           ├── shift_dropdown.dart              👈 Dropdown for shift selection
│           ├── site_dropdown.dart               👈 Dropdown for site selection
│           ├── site_incharge_dropdown.dart      👈 Dropdown for site incharge
│           ├── submit_cancel_buttonn.dart       👈 Submit & Cancel button set
│           ├── title_textfiled.dart             👈 Title input text field
│           ├── type_dropdown.dart               👈 Dropdown for type selection
│           └── view_image.dart                  👈 Fullscreen image viewer
```
