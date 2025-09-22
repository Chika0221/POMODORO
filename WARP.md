# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

Project overview and architecture
- Toolkit: Flutter (Dart), with Android, iOS, and Web targets present.
- Entry point: lib/main.dart defines MaterialApp -> MyHomePage (StatefulWidget).
- UI: MyHomePage builds a Scaffold body that renders a 3D model via Flutter3DViewer.obj from the flutter_3d_controller package. A Flutter3DController is created in initState but not yet wired to the viewer.
- State: Simple local state via setState; no routing or external state management.
- Assets: A .obj model exists at assets/indoor plant_02.obj. pubspec.yaml declares assets/models as the only asset directory. Either move the model under assets/models or include assets/ (or the specific file) in pubspec.yaml so the asset loads at runtime.
- Tests: test/widget_test.dart is the default counter smoke test (expects a '+' button). The current UI does not expose an add button, so this test will fail as-is; update the test or UI accordingly.
- Linting: analysis_options.yaml enables the flutter_lints ruleset (v5 via pubspec). No custom lint overrides are configured.

Environment
- Dart SDK constraint: ^3.7.2 (ensure your Flutter SDK bundles a compatible Dart version).

Common commands
- Get dependencies: flutter pub get
- Analyze (static checks): flutter analyze
- Format code: dart format .
- Run app (choose a device):
  - List devices: flutter devices
  - Android emulator (example): flutter run -d <device_id>
  - Web (Chrome on Windows): flutter run -d chrome
- Run all tests: flutter test
- Run a single test file: flutter test test/widget_test.dart
- Run tests by name: flutter test --name "Counter increments smoke test"
- Build release artifacts:
  - Android APK: flutter build apk --release
  - Web: flutter build web --release

Optional utilities present in pubspec
- import_sorter: dart run import_sorter:main
- rename_app: dart run rename_app:main --help (use to rename app/bundle identifiers when needed)

Repository layout (high-level)
- lib/: Dart source (main.dart is the sole app entry point)
- test/: Widget tests (currently default template)
- assets/: 3D model(s) and static assets
- android/, ios/: Platform build configuration
- web/: Web index and PWA assets
