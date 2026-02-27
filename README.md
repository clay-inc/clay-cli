# @clayhq/clay

Command-line interface for [Clay](https://clay.earth) — your personal CRM.

## Installation

```bash
npm install -g @clayhq/clay-cli
```

Or run directly with npx:

```bash
npx @clayhq/clay-cli <command>
```

## Authentication

Log in with your Clay account:

```bash
clay login
```

This opens your browser to authorize the CLI. Once authenticated, your credentials are stored locally at `~/.config/clay.json`.

```bash
clay status   # Check login status
clay logout   # Remove stored credentials
```

## Commands

### Contacts

```bash
clay contacts:search --name "Jane Doe"
clay contacts:search --keywords "designer" --work-history-company "Google"
clay contact --contact-id 123
clay contacts:create --first-name "Jane" --last-name "Doe" --email "jane@example.com"
clay contacts:update --contact-id 123 --title "Senior Designer"
clay contacts:archive --contact-ids 123
clay contacts:restore --contact-ids 123
clay contacts:merge --contact-ids 123,456
```

### Notes

```bash
clay notes:create --contact-id 123 --content "Met at the conference"
clay notes --start 2025-01-01 --end 2025-12-31
```

### Groups

```bash
clay groups
clay groups:create --title "Investors"
clay groups:update --group-id 5 --add-contact-ids 123,456
```

### Events & Emails

```bash
clay events --start 2025-01-01 --end 2025-01-31
clay events:upcoming
clay emails --start 2025-01-01 --end 2025-01-31
clay emails:recent
```

### Reminders

```bash
clay reminders:recent
clay reminders:upcoming
```

## Output Formats

All commands default to JSON. Use `--format` to change:

```bash
clay contacts:search --name "Jane" --format json   # default
clay contacts:search --name "Jane" --format csv
clay contacts:search --name "Jane" --format tsv
```

## Requirements

- Node.js 18+
- A [Clay](https://clay.earth) account

## License

Copyright Clay
