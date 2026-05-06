# @meshhq/mesh-cli

Command-line interface for [Mesh](https://me.sh) — your personal CRM.

## Installation

```bash
npm install -g @meshhq/mesh-cli
```

Or run directly with npx:

```bash
npx @meshhq/mesh-cli <command>
```

## Authentication

Log in with your Mesh account:

```bash
mesh login
```

This opens your browser to authorize the CLI. Once authenticated, your credentials are stored locally at `~/.config/mesh-cli.json`.

```bash
mesh status   # Check login status
mesh logout   # Remove stored credentials
```

## Commands

### Contacts

```bash
mesh contacts:search --name "Jane Doe"
mesh contacts:search --keywords "designer" --work-history-company "Google"
mesh contact --contact-id 123
mesh contacts:create --first-name "Jane" --last-name "Doe" --email "jane@example.com"
mesh contacts:update --contact-id 123 --title "Senior Designer"
mesh contacts:archive --contact-ids 123
mesh contacts:restore --contact-ids 123
mesh contacts:merge --contact-ids 123,456
```

### Notes

```bash
mesh notes:create --contact-id 123 --content "Met at the conference"
mesh notes --start 2025-01-01 --end 2025-12-31
```

### Groups

```bash
mesh groups
mesh groups:create --title "Investors"
mesh groups:update --group-id 5 --add-contact-ids 123,456
```

### Events & Emails

```bash
mesh events --start 2025-01-01 --end 2025-01-31
mesh events:upcoming
mesh emails --start 2025-01-01 --end 2025-01-31
mesh emails:recent
```

### Reminders

```bash
mesh reminders:recent
mesh reminders:upcoming
```

## Output Formats

All commands default to JSON. Use `--format` to change:

```bash
mesh contacts:search --name "Jane" --format json   # default
mesh contacts:search --name "Jane" --format csv
mesh contacts:search --name "Jane" --format tsv
```

## Requirements

- Node.js 18+
- A [Mesh](https://me.sh) account

## License

Copyright Mesh
