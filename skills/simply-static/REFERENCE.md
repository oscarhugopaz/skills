# Simply Static WP-CLI Reference

Source: https://docs.simplystatic.com/article/51-working-with-wp-cli

Last source update shown by Simply Static docs: February 15, 2025.

## Requirement

The WP-CLI integration documented by Simply Static requires Simply Static Pro. Run these commands from the WordPress installation directory, or use the path/url flags required by the local WP-CLI environment.

## Command Overview

All documented commands use the `simply-static` WP-CLI namespace:

```bash
wp simply-static
```

Run that command locally to inspect the installed plugin's help output.

## License Activation

Activate a Simply Static Pro license:

```bash
wp simply-static activate --license=YOUR_LICENSE_KEY
```

## Static Exports

Run a full static export:

```bash
wp simply-static run
```

Run a single export for one post ID:

```bash
wp simply-static run --single=123
```

`123` is the WordPress post ID to export.

Run a build export by build ID:

```bash
wp simply-static run --build=123
```

Run an update export:

```bash
wp simply-static run --update=true
```

## Include Files And Pages

Inspect include commands:

```bash
wp simply-static includes
```

Documented usage:

```bash
wp simply-static includes add_file <path> [--blog_id=<blog_id>]
wp simply-static includes add_url <url> [--blog_id=<blog_id>]
wp simply-static includes list_files [--blog_id=<blog_id>]
wp simply-static includes list_urls [--blog_id=<blog_id>]
wp simply-static includes remove_file <path> [--blog_id=<blog_id>]
wp simply-static includes remove_url <url> [--blog_id=<blog_id>]
```

Use absolute URLs for `add_url`; do not pass only a relative path.

Example:

```bash
wp simply-static includes add_url https://example.com/special-page/
```

Use `--blog_id=<blog_id>` on multisite when changing settings for one subsite.

## Exclude Pages

Inspect exclude commands:

```bash
wp simply-static excludes
```

Documented usage:

```bash
wp simply-static excludes add_url <url> [--do_not_follow=<do_not_follow>] [--do_not_save=<do_not_save>] [--blog_id=<blog_id>]
wp simply-static excludes list_urls [--blog_id=<blog_id>]
wp simply-static excludes remove_url <url> [--blog_id=<blog_id>]
wp simply-static excludes update_url <url> [--do_not_follow=<do_not_follow>] [--do_not_save=<do_not_save>] [--blog_id=<blog_id>]
```

Example:

```bash
wp simply-static excludes add_url https://example.com/private/ --do_not_follow=true --do_not_save=true
```

Use `--blog_id=<blog_id>` on multisite when changing settings for one subsite.

## Forms

Inspect form commands:

```bash
wp simply-static forms
```

Documented usage:

```bash
wp simply-static forms add_form [--blog_id=<blog_id>]
wp simply-static forms list [--blog_id=<blog_id>]
```

`add_form` is interactive. The documented prompt flow asks for:

- Title, for example `My Form`
- Tool: `cf7`, `gravity_forms`, or `external`
- Form ID, required for a form plugin, for example `12`
- Subject, required for a form plugin
- Name attributes as a comma-separated list, for example `myfield-1,myfield-2`
- Message body, which can use HTML
- Recipient email address

Example command:

```bash
wp simply-static forms add_form
```

## Options

Inspect option update commands:

```bash
wp simply-static update
```

Documented usage:

```bash
wp simply-static update deployment <command>
wp simply-static update general <command>
```

The source documentation says the CLI currently documents option updates for `deployment` and `general`; more advanced areas such as forms and search have interactivity attached.

Run local help for the installed version before changing settings:

```bash
wp simply-static update deployment
wp simply-static update general
```

## Import And Export Settings

Export settings as JSON:

```bash
wp simply-static export
```

Import settings from a JSON string or from a filesystem file:

```bash
wp simply-static import --json=JSON_STRING --file=ABSOLUTE_FILE_PATH
```

Use an absolute path for `--file`. The source documentation renders typographic dashes in the import example; convert those to normal double hyphens before running the command.
