# Sana

Sana is a Flutter application for personal health records and smart medication reminders.

**Canonical repository:** https://github.com/riobase/sana  
**Live web app:** https://riobase.github.io/sana/

This repository is the source of truth for Sana. App sharing links, the published Flutter site, and the PWA launch path are configured for the `riobase` project URL.

## Local development

1. Install the Flutter stable SDK.
2. Fetch dependencies:

   ```sh
   flutter pub get
   ```

3. Run the app locally:

   ```sh
   flutter run
   ```

## GitHub Pages deployment

The `main` branch is the source of truth for the web deployment. GitHub Actions builds the Flutter app with the required project-site base path, uploads `build/web` as a Pages artifact, and publishes it through the `github-pages` environment using GitHub's Pages deployment action:

```sh
flutter build web --release --base-href /sana/
```

Keep the `/sana/` base path unchanged while the repository is named `sana`. It is required for Flutter's generated JavaScript, assets, service worker, manifest, and route loading to resolve correctly at the project Pages URL. The workflow verifies the generated build and then checks the live homepage, PWA manifest, service worker, and critical Flutter assets.

The deployment workflow builds directly from this repository; it does not download or overwrite source code from an external server.
