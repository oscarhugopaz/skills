---
name: simply-static
description: Manage Simply Static and Simply Static Pro from WordPress with WP-CLI, including license activation, static exports, include/exclude rules, forms, options, and JSON settings import/export. Use when working with Simply Static, static WordPress exports, or `wp simply-static` commands.
---
# Simply Static

Use this skill to operate the Simply Static WordPress plugin through WP-CLI. The WP-CLI integration documented by Simply Static requires Simply Static Pro.

Source documentation and detailed command reference: [REFERENCE.md](REFERENCE.md)

## Before Running Commands

1. Work from the WordPress installation directory, or pass the appropriate WP-CLI path/url flags used by the local environment.
2. Confirm WP-CLI can load WordPress:

```bash
wp core version
```

3. Confirm Simply Static commands are available and inspect the local command help:

```bash
wp simply-static
```

Prefer the local help output over memorized flags when there is a mismatch, because plugin versions can differ.

## Common Commands

```bash
# Activate a Simply Static Pro license.
wp simply-static activate --license=YOUR_LICENSE_KEY

# Run exports.
wp simply-static run
wp simply-static run --single=123
wp simply-static run --build=123
wp simply-static run --update=true

# Export/import settings as JSON.
wp simply-static export
wp simply-static import --json=JSON_STRING --file=/absolute/path/to/settings.json
```

Use normal double hyphens for flags; see [REFERENCE.md](REFERENCE.md) for full usage.

## Include Rules

```bash
# Inspect include commands.
wp simply-static includes

# Use absolute URLs when adding URLs, not relative paths.
wp simply-static includes add_url https://example.com/special-page/
wp simply-static includes list_urls
wp simply-static includes remove_url https://example.com/special-page/

# Manage included files by filesystem path.
wp simply-static includes add_file /absolute/path/to/file.pdf
wp simply-static includes list_files
wp simply-static includes remove_file /absolute/path/to/file.pdf
```

On multisite, add `--blog_id=<blog_id>` when targeting one subsite.

## Exclude Rules

```bash
# Inspect exclude commands.
wp simply-static excludes

# Add, update, list, or remove excluded URLs.
wp simply-static excludes add_url https://example.com/private/ --do_not_follow=true --do_not_save=true
wp simply-static excludes list_urls
wp simply-static excludes update_url https://example.com/private/ --do_not_follow=true --do_not_save=false
wp simply-static excludes remove_url https://example.com/private/
```

On multisite, add `--blog_id=<blog_id>` when targeting one subsite.

## Forms And Options

```bash
# List form commands or start the interactive form setup.
wp simply-static forms
wp simply-static forms list
wp simply-static forms add_form
```

`add_form` prompts for fields such as title, tool, form ID, subject, field names, message HTML, and recipient email.

```bash
# Inspect option update commands. Documented groups: deployment and general.
wp simply-static update
wp simply-static update deployment <command>
wp simply-static update general <command>
```

Run `wp simply-static update <group>` locally to see the concrete subcommands and flags for the installed version.
