# APK Auditor

Android APK security analysis tool that runs in the browser. Drop an APK file, it decompiles the DEX, parses the manifest, scans for issues, and lets you browse the code. Nothing gets uploaded anywhere.

## How to use

Just open `index.html` in Chrome/Firefox/Edge. Drag and drop an APK. That's it.

If you want to serve it locally:
```
python -m http.server 8000
```

## What it does

- Decompiles DEX files to Java pseudocode and Smali (no JADX/apktool needed)
- Scans for hardcoded secrets, weak crypto, insecure HTTP, exported components, WebView vulns, intent issues, etc (80+ checks)
- Parses binary AndroidManifest.xml and resources.arsc
- Shows exported components with ADB commands to test them
- Reads signing certificates, catches debug keys and weak algorithms
- Detects known SDKs and trackers (Firebase, Facebook, Sentry, etc)
- Exports PDF reports with findings mapped to CWE/OWASP/MASVS
- Browses all files inside the APK with syntax highlighting

Everything runs client-side in JavaScript. The APK never leaves your machine.

## Project structure

```
index.html         - the UI
apk-analyzer.js    - all the analysis logic
lib/               - jszip and jspdf
```

## Credits

Built by Sandeep Wawdane
