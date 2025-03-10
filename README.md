# Flutter AGL Demo

A simple Flutter application for Automotive Grade Linux (AGL) that displays your name and a button to show an image.

## Overview

This repository contains a Flutter application specifically designed to run on the AGL platform. The application demonstrates integration of Flutter with AGL's salmon branch. It features a minimal UI that displays a name and a button that, when clicked, toggles the visibility of an image.

## Features

- Simple Flutter UI optimized for automotive displays
- Integration with AGL framework
- Button-activated image display
- Easily customizable codebase

## Prerequisites

To build and deploy this application, you will need:

- Ubuntu 22.04 LTS (Jammy Jellyfish)
- Git
- Python 3 and pip
- [meta-flutter/workspace-automation](https://github.com/meta-flutter/workspace-automation)
- Yocto Project tooling
- AGL salmon branch

## Integration with AGL

This app is designed to be integrated with AGL using the provided Yocto layer. The companion meta layer repository [meta-flutter-agl-demo](https://github.com/yourusername/meta-flutter-agl-demo) contains:

- Custom Yocto layer setup
- Recipe for building and installing this Flutter app
- Configuration for integration with AGL's salmon branch

## Usage

Once deployed to an AGL system (or QEMU emulator):

1. Launch the app from the AGL home screen or app launcher
2. You will see your name displayed on the screen
3. Click the "Show Image" button to display an image
4. Click the button again to hide the image

## Customization

### Changing the Name Display

Edit the `lib/main.dart` file and modify the following line:

```dart
const Text(
  'Your Name',  // Replace with your desired name
  style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
),
```

### Changing the Image

To use a custom image, add it to the assets folder and update the `pubspec.yaml` file to include it:

```yaml
flutter:
  assets:
    - assets/your_image.png
```

Then update the image widget in `lib/main.dart`.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- [Automotive Grade Linux (AGL)](https://www.automotivelinux.org/)
- [Flutter](https://flutter.dev/)
- [meta-flutter](https://github.com/meta-flutter)

## Screenshots

*Add screenshots of your application running on AGL here*