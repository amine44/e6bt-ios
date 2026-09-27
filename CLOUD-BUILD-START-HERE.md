# Build E6BT iOS from Windows

This archive is source and configuration, not an IPA. A cloud build has not yet run.

1. Create a PRIVATE GitHub repository, for example e6bt-ios. Extract this ZIP and upload its contents, including ios/, www/, package.json, package-lock.json, capacitor.config.json and codemagic.yaml, to the repository root. Do not upload the ZIP itself as the only repository file.
2. Sign in to Codemagic and connect only this repository. Choose the YAML configuration and workflow E6BT iOS signed build.
3. In your Apple Developer account register an explicit App ID com.e6bt.pilot.twa. Create the matching iOS app in App Store Connect. If that ID is unavailable in your account, stop and change the project before building.
4. Configure Codemagic's Apple signing integration. Its code-signing identities must contain an Apple Distribution certificate WITH its private key and an App Store provisioning profile matching com.e6bt.pilot.twa. Codemagic can generate/fetch signing assets through its App Store Connect integration; follow the linked official guide. Add Apple credentials only through Codemagic's secure integration/signing UI, never GitHub or chat.
5. Run the workflow manually after confirming the build-service plan and any charges. It installs the locked packages, syncs the bundled app, applies the signing profile and builds an IPA artifact.
6. Review the build results. Then configure App Store Connect upload in Codemagic and upload for TestFlight. Publishing is deliberately not enabled in this configuration; nothing is automatically submitted to Apple or external testers.

The first cloud build must validate Xcode compilation and signing. Test on an actual iPhone through TestFlight before production. This project also targets iPad, which needs its own checks and screenshots. The build counter assumes this is a new iOS app; if you already uploaded builds, set the next build number higher than the existing Apple build number.

No Android keystore or Apple credentials are included in this archive. Android signing keys cannot sign an iOS app.

Official setup: https://docs.codemagic.io/yaml-quick-start/building-an-ionic-app/
See IOS-START-HERE.md for current feature limitations and device-test requirements.
