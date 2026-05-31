# SpendWise iOS

<p align="center">
  <img src="First_App/First_App/Assets.xcassets/AppIcon.appiconset/icon_1024.png" alt="SpendWise Logo" width="180" style="border-radius: 36px;"/>
</p>

<p align="center">
  <strong>A premium, modern, and privacy-focused personal expense tracker built natively for iOS with SwiftUI and Combine.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-iOS%2017%2B-000000?logo=apple&logoColor=white" alt="Platform: iOS 17+" />
  <img src="https://img.shields.io/badge/Language-Swift%205.9-F05138?logo=swift&logoColor=white" alt="Language: Swift" />
  <img src="https://img.shields.io/badge/UI-SwiftUI-007AFF?logo=swift&logoColor=white" alt="UI: SwiftUI" />
  <img src="https://img.shields.io/badge/Architecture-MVVM-FF6F00?logo=xcode&logoColor=white" alt="Architecture: MVVM" />
</p>

---

## 🌟 Overview

**SpendWise iOS** is a native, highly responsive financial companion for iPhone, translated and optimized from the Android Jetpack Compose version. It runs completely locally, providing a fast, secure expense management flow with 100% data privacy.

The application leverages a clean MVVM structure and Xcode 16's file system synchronization. Featuring dynamic slate-navy elements, local push notifications, interactive category limit thresholds, a built-in input calculator, and full CSV import/export data portability, SpendWise keeps your budget under control.

---

## ✨ Features

### 📊 1. Dynamic Financial Dashboard
* **Real-time Balance Calculations:** Instantly computes your total budget, total spent, and remaining balance.
* **Aggregated Progress Bar:** A prominent top balance progress card displaying your budget utilization.
* **Interactive Category Chips:** Fast horizontal filter ribbon to slice your transactions by selecting category icons (e.g. food 🍱, shopping 🛍️, bills 📱).
* **Dynamic Time Range Ribbons:** Instantly filter transactions across All, Weekly, Monthly, Yearly, or custom date ranges.

### 🏷️ 2. Customizable Category Limits
* **Visual Progress Cards:** Monitor individual category margins using progress cards that automatically shift color:
  * 🟢 **Safe (< 60% limit):** Expenses are well under control.
  * 🟡 **Warning (60% - 90% limit):** Nearing the category cap.
  * 🔴 **Danger (> 90% limit):** Threshold breached or exceeded.
* **Granular Configuration:** Adjust monthly limit caps directly within Xcode’s borderless button-protected category settings list.

### 🧮 3. Integrated Input Calculator
* **Arithmetic Sheet:** A custom interactive calculator overlay designed to solve basic operations (`+`, `-`, `×`, `÷`) and directly insert results into the budget or expense input fields.
* **Dismiss Safely:** Dismisses automatically upon confirming calculation results.

### 🔔 4. Local Push Notifications & Daily Reminders
* **Spending Warnings:** Immediately dispatches a native banner warning when an added transaction exceeds a category's budget.
* **Custom Daily Alerts:** Schedules custom repeating calendar alarms (e.g., `20:00`) using `UNUserNotificationCenter` to remind you to log daily expenditures.

### 🗑️ 5. Soft-Delete Trash System
* **Expense & Category Segments:** Segregated list views protecting against accidental deletions.
* **Restore & Purge:** Instantly restore items to the active ledger/list, permanently delete specific items, or clear all.
* **30-Day Auto Purge:** Background logic automatically cleans up items older than 30 days on application startup.

### 💾 6. Data Portability (Backup & Restore)
* **CSV Export:** Package and share settings, global budgets, categories, and full transaction history.
* **CSV Parser:** Seamlessly import backing sheets to restore your ledger.
* **Wipe Safeguard:** Enforces creating a backup export before executing a full application factory data reset.

---

## 🛠️ Technical Architecture & Stack

SpendWise iOS is built utilizing standard Apple frameworks and modern architecture:

* **SwiftUI:** Declarative UI layouts designed for iOS 17+.
* **Combine Framework:** Orchestrates reactive unidirectional flows between the repository, ViewModel, and views using `@Published` state publishers.
* **UserDefaults Storage:** High-performance local storage wrapping customized serialization helper techniques to save and retrieve state without database overhead.
* **UserNotifications Framework:** Triggers instant local budget alert banners and schedules background daily reminders.

---

## 📂 Codebase Tour

```
First_App/
│
├── First_App/
│   ├── Assets.xcassets/          # App icon assets and Slate-Navy color catalogs
│   │
│   ├── Views/
│   │   ├── Components.swift      # Custom reusable cards (CategoryStatCard, ExpenseCard, CalculatorSheet)
│   │   └── Sheets.swift          # Form sheets (AddExpenseSheet, SettingsSheet, TrashSheet, BackupRestoreSheet)
│   │
│   ├── Models.swift              # Decoupled domain models (Category, Expense, TrashExpense, TrashCategory, etc.)
│   ├── DataRepository.swift      # Local persistence interface (UserDefaults serialization & 30-day auto-purge)
│   ├── MainViewModel.swift       # Reactive state aggregation, date ranges, and CSV import/export parsing
│   ├── Theme.swift               # Hex color converter extension and AppColors slate system mappings
│   ├── NotificationManager.swift # Local alerts scheduler (daily repeating calendar triggers and instant banners)
│   ├── ContentView.swift         # Core layout containing the Dashboard and Limits tabs with custom Tab Bar
│   └── First_AppApp.swift        # Main App entrypoint initializing notification authorizations
│
└── First_App.xcodeproj           # Xcode project package
```

---

## 🚀 Getting Started

### Prerequisites
* **macOS:** macOS Sonoma or newer.
* **Xcode:** Xcode 15 or newer (Xcode 16 recommended for file system synchronization compatibility).
* **Simulator:** iOS 17.0+ Simulator.

### Building & Running

1. **Open the Project in Xcode:**
   * Double-click `First_App.xcodeproj` or open Xcode and choose **File > Open**, navigating to:
     `/Users/arpandutta/Desktop/test/IOS_Project/first_app/First_App/First_App.xcodeproj`
2. **Select Destination:**
   * Select an iOS Simulator device (e.g. *iPhone 17*) from the scheme/device selection bar at the top.
3. **Compile and Run:**
   * Press **`Cmd + R`** (or click the play icon `▶` in the top left) to build and launch the application.

### Command Line Build
To verify the build using standard command-line tools:
```bash
cd First_App
xcodebuild -project First_App.xcodeproj -scheme First_App -sdk iphonesimulator clean build
```

---

## 💡 Troubleshooting

### Simulator App Icon Not Showing
If the iOS Simulator continues to show the default grid wireframe rather than the compiled icon:
1. Long-press the `SpendWise` icon on the simulator screen and select **Delete App**.
2. Clean the build folder in Xcode by pressing **`Cmd + Shift + K`**.
3. Re-run the application (**`Cmd + R`**) to force iOS to rebuild its launch services cache.

---

## 📄 License

```
Copyright 2026 SpendWise Authors

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
