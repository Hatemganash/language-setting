🌍 Language Switcher for iOS (Swift)
This repo provides a simple and reusable way to support runtime language switching in iOS apps using Arabic and English. It supports RTL (Right-to-Left) and LTR (Left-to-Right) layout direction updates and dynamically changes the app language without restarting the entire app.

📦 Features
🔁 Change app language at runtime

🔄 Automatically updates UI direction (RTL / LTR)

🌐 Supports Arabic (ar) and English (en)

✅ Based on native .lproj localization files

🚫 Does not rely on String category extensions

🚀 How to Use
1. Add Language.swift to Your Project
Just drag and drop the Language.swift file into your project.

2. Create Localizable.strings Files
❗️ Important: This system uses the official .strings files and does not support hardcoded string extensions like "Hello".localized.

You must create:

en.lproj/Localizable.strings

ar.lproj/Localizable.strings

Example: en.lproj/Localizable.strings
swift
Copy
Edit
"Logout" = "Logout";
"Change Language" = "Change Language";
"Setting" = "Setting";
Example: ar.lproj/Localizable.strings
swift
Copy
Edit
"Logout" = "تسجيل الخروج";
"Change Language" = "تغيير اللغة";
"Setting" = "الإعدادات";
🧠 Changing the Language
Call this anywhere (e.g. in settings menu):

swift
Copy
Edit
let newLang = Language.currentLanguage().contains(Language.Languages.ar) ? Language.Languages.en : Language.Languages.ar
Language.setAppLanguage(lang: newLang)
Then reset your root view controller:

swift
Copy
Edit
let sceneDelegate = UIApplication.shared.connectedScenes.first?.delegate as? SceneDelegate
sceneDelegate?.window?.rootViewController = YourMainVC()
sceneDelegate?.window?.makeKeyAndVisible()
💡 Tips
Use NSLocalizedString or String(key).localized only if your project uses .strings files.

Avoid hardcoded extensions like:

swift
Copy
Edit
extension String {
    var localized: String {
        return NSLocalizedString(self, comment: "")
    }
}
as they won’t fully support the runtime language switching mechanism used here.

🛠 Requirements
iOS 13.0+

Swift 5+

