# Nextcloud - Domain Theming
Customizes the appearance of **Nextcloud** according to the trusted domain from which it is being accessed.

_Note: This application is intended for use by a system administrator as it has no user interface._

Supports **Nextcloud 31-33** and follows the PHP versions supported by those server releases, including **PHP 8.4**.

### Important Update for Nextcloud 33+

Nextcloud 33 removes the ScssPhp package. I don't plan to include it as it's very easy to set up a "watcher" and automatically compile the SCSS, or just write plain css...

The `scss` variable in the configuration was replaced with `css` and a new folder with this name was added. The old SCSS folder will remain in the same place.

## Installation

### Automatic installation (recommended)

Just install it from your **Nextcloud** application catalogue.

### Manual installation

Clone this repository into your **Nextcloud** apps directory using the local app id as the folder name:

```bash
cd /var/www/nextcloud/site/apps/
git clone https://github.com/mediabox-cl/nextcloud-theming-domain theming_domain_custom
```

Keep the `.git` directory in the installed app folder. Nextcloud's update notification app ignores custom apps that are deployed as Git checkouts; if the app is copied from a tarball or ZIP without `.git`, the updater will still look for a matching App Store release and report `Domain Theming Custom` as missing a compatible version.

Install it as usual from admin app list or CLI with:

```bash
cd ..
sudo -u www-data php occ app:install theming_domain_custom
sudo -u www-data php occ app:enable theming_domain_custom
```

If you already copied the app without Git metadata, replace that copy with a clone or create Git metadata in the installed app directory before running the Nextcloud update check again.

# Configuration

After installing the application, a new configuration file called `theming.domain.config.php` will be created inside the `config` directory. You can use this file to customize the trusted domains (`trusted_domains`) configured in **Nextcloud's** `config.php` file.

### Configuration keys:
`version (integer|string)` = CSS Version (Cache Buster)  
`variables (array)` = Theme variables. Can be used to override the **Nextcloud** Theme Variables (`:root {...}`).  
`css (string)` = Path to a custom css file relative to the `css` folder inside the APP main folder (`theming_domain_custom`).

_Note: None of these keys are mandatory, you can use them or not._

_Note: The local app id is `theming_domain_custom`, but the configuration key intentionally remains `theming_domain` so existing installations can reuse their current `theming.domain.config.php` unchanged._

### Configuration example:

```
<?php

# Domain Theming APP Config file (theming.domain.config.php).

$CONFIG = array(
    'theming_domain' => array( // APP Config Key
        'cloud.domain.tld' => array( // Trusted Domain
            'version' => 1, // CSS Version
            'variables' => array( // Variables to be overrided
                '--image-background-default' => "url('/apps/theming/img/background/tommy-chau-already.jpg')"
            ),
            'css' => '/default/style.css' // Custom CSS file
        ),
        'cloud.domain2.tld' => array(
            'version' => 355,
            //...
        )
    )
);
```

## Thanks to:

- The **Nextcloud** community and developers.
