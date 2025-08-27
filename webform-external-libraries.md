# Webform Libraries Installation Guide

This document provides instructions for downloading and installing external libraries for the Webform module in Drupal using Composer, ensuring a maintainable and Drupal-standard approach.

## Step 1: Install the Composer Merge Plugin
To merge the Webform module’s `composer.libraries.json` with your project’s `composer.json`, install the `wikimedia/composer-merge-plugin`:

```bash
composer require wikimedia/composer-merge-plugin
```

## Step 2: Configure composer.json for Webform Libraries
Edit your Drupal project’s `composer.json` to include the Webform module’s `composer.libraries.json`. Add the following to the `"extra"` section:

```json
"merge-plugin": {
    "include": [
        "web/modules/contrib/webform/composer.libraries.json"
    ]
}
```

This ensures Composer processes Webform’s library dependencies (e.g., CKEditor, Algolia Places, Choices).

## Step 3: Download Webform Libraries
Run the following command to download Webform libraries to `web/libraries`:

```bash
composer update drupal/webform --with-dependencies
```

This installs libraries like CKEditor, Choices, and others into `web/libraries`.

## Step 5: Clear Drupal Cache
After installing libraries, clear Drupal’s cache to ensure proper integration:

```bash
drush cache:rebuild
```

Optionally, run `drush updb` to update the database if needed.

## Step 6: Verify Installation
- Check `web/libraries` to ensure Webform libraries (e.g., `ckeditor`, `choices`) are present.
- Visit `/admin/reports/status` in your Drupal admin interface to confirm that all required Webform libraries are detected and not listed as missing.
