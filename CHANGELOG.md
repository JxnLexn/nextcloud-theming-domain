## 33.0.2

- Publish a fresh release without an explicit PHP upper bound so Nextcloud 32.0.9 installations running PHP 8.4 can install and enable the app.
- Switch the app metadata license identifier to the SPDX-compatible `AGPL-3.0-or-later` value required for apps targeting Nextcloud 31+.

## 33.0.1

- Remove the explicit PHP dependency from `appinfo/info.xml` so the app can follow the PHP versions supported by Nextcloud 31-33, including PHP 8.4.
- Tighten a few PHP method signatures and controller property types for cleaner compatibility with newer PHP runtimes.

## 33.0.0

- Bump version to 33.0.0 and max-version to 33 to make it compatible with Nextcloud 33+.
- Remove SCSS support because Nextcloud 33 remove ScssPhp package.
- Replace scss variable with css.

## 31.0.1

- Initial release
