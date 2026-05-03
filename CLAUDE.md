# launcher — Cutefish Application Launcher

## Purpose
Full-screen application launcher (GNOME Activities / macOS Launchpad style). Displays all installed applications in a grid with search and category filtering.

## Build
```bash
cmake -B build -DCMAKE_INSTALL_PREFIX=/usr && cmake --build build && sudo cmake --install build
```

## Dependencies
- Qt6 (Core, Widgets, DBus, Quick, QuickControls2, LinguistTools)
- KDE Frameworks 6 (KF6WindowSystem)

## Structure
- `src/launcher.cpp/h` — main launcher window
- `src/launchermodel.cpp/h` — application model
- `src/appmanager.cpp/h` — application management
- `src/appitem.cpp/h`, `src/iconitem.cpp/h` — UI items
- `src/applicationlistmodel.cpp/h` — list model
- `src/pagemodel.cpp/h` — paging model
- `src/listmodelmanager.cpp/h` — model management
- `src/desktopproperties.cpp/h` — desktop file parsing
- `src/processprovider.cpp/h` — running process tracking
- `src/iconthemeimageprovider.cpp/h` — icon theming
- `src/ucunits.cpp/h` — unit conversion
- `qml/main.qml`, `qml/AllAppsView.qml`, `qml/CategoryView.qml`, `qml/GridItemDelegate.qml` — QML UI
- `src/com.cutefish.Launcher.xml` — D-Bus adaptor (LauncherAdaptor)

## Install Targets
- Binary → `${CMAKE_INSTALL_BINDIR}`
- Translations → `/usr/share/cutefish-launcher/translations/`

## Qt5→Qt6 Migration Notes
- Qt5 → Qt6, KF5 → KF6
- `geometryChanged` → `geometryChange` (Qt6 rename)
- `KX11Extras::setState` guarded with xcb platform check
- `setGeometry()` won't work on Wayland (needs layer-shell or showFullScreen)

## Status
✅ Ported, built, installed, pushed (github.com/ali-soomro)
