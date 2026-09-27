# E6BT iOS / TestFlight preparation

This is an Xcode source project, not a compiled or signed IPA. It has not yet been built or tested on iOS.

- Bundle ID: `com.e6bt.pilot.twa` (register this exact ID in your Apple developer account, or change both Xcode and Capacitor configuration before first publication).
- Display name: E6BT.
- Version: 1.0, build 1.
- Minimum iOS: 15.0.
- Capacitor Swift package: 8.5.2, resolved through Swift Package Manager.
- 20 bundled HTML tools, shared branding/footer, local favourites, and foreground content refresh.
- Branded 1024-pixel opaque icon installed in the asset catalog.
- No ads or push notifications in this version.

## On a Mac

1. Install a current stable Xcode supported by App Store Connect (Capacitor 8 requires Xcode 26 or newer). Open Xcode once and install its required components.
2. Extract this project. Open `ios/App/App.xcodeproj`. Let Xcode resolve the Swift packages; internet is needed for this initial setup.
3. Select the App target, then Signing & Capabilities. Choose your Apple Developer team and enable automatic signing. Confirm the bundle ID is available in your account. No Apple signing identity or team is configured in this archive.
4. Run on an iPhone simulator and a physical iPhone. Check navigation, keyboard scrolling, safe areas, all calculators, offline launch, saved values, file import/export and external links. Also test iPad because the project includes iPad support. Do not advertise device compatibility before testing it.
5. In App Store Connect create an iOS app record using the same registered bundle ID. Set the intended paid price before launch; complete privacy, age rating, export compliance and other requested declarations accurately. Android signing keys do not apply to iOS.
6. In Xcode choose a generic iOS device destination, Product > Archive, then Distribute App > App Store Connect. Upload after validation.
7. After processing, configure TestFlight beta details and testers. External testing can require Apple's beta review. Collect feedback before production submission.

The bundled assets are already copied into the iOS project, so Node is not needed merely to open this snapshot in Xcode. For later web changes, install Node 22+, run `npm ci` in the project root, then `npx cap sync ios` before building.

## Important current limits

Live weather and full blog pages open online. Pasted-report decoders and local calculators are bundled, but their operation and accuracy on iOS still need device testing. Notification delivery and background daily refresh are not implemented. Leaving a tool can reset unsaved inputs. Aircraft profiles need verification against the specific aircraft documentation.

The included browser screenshots are not iPhone or iPad screenshots. Capture screenshots on the Apple devices/simulators after the app is running.

References:
- https://capacitorjs.com/docs/ios
- https://developer.apple.com/help/app-store-connect/manage-builds/upload-builds
- https://developer.apple.com/testflight/
