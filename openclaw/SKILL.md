---
name: Mesh
description: Search, manage, and organize your contact network via the Mesh CLI.
homepage: https://me.sh
metadata:
  {
    "openclaw":
      {
        "emoji": "🕸️",
        "os": ["darwin", "linux"],
        "requires": { "bins": ["mesh"] },
        "install":
          [
            {
              "id": "npm",
              "kind": "npm",
              "package": "@meshhq/mesh-cli",
              "bins": ["mesh"],
              "label": "Install mesh (npm)",
            },
          ],
      },
  }
---

# Mesh

Use `mesh` to search, create, update, and manage your personal contact network from the command line.

## Requirements

- A Mesh account ([me.sh](https://me.sh))
- Authenticate before using any commands: `mesh login`

## Authentication

Log in (opens browser for OAuth):

```bash
mesh login
```

Check authentication status:

```bash
mesh status
```

Log out:

```bash
mesh logout
```

Credentials are stored in `~/.config/clay.json`.

## Output Formats

All data commands support `--format` to control output:

- `json` (default) — Pretty-printed JSON
- `csv` — Comma-separated values
- `tsv` — Tab-separated values

```bash
mesh contacts:search --name "Alice" --format csv
mesh emails:recent --format tsv
```

## Contacts

Get a contact by ID:

```bash
mesh contact --contact-id 12345
```

Search contacts:

```bash
mesh contacts:search --name "Jane Smith"
mesh contacts:search --work-history-company "Acme" --work-history-active true
mesh contacts:search --education-history-school "MIT"
mesh contacts:search --location-latitude 37.7749 --location-longitude -122.4194 --location-distance 50
mesh contacts:search --last-email-date-gte "2025-01-01" --sort-field "last_email_date" --sort-direction "desc"
mesh contacts:search --group-ids "starred" --limit 10
mesh contacts:search --keywords "investor" --include-fields "name,email,title"
```

Create a contact:

```bash
mesh contacts:create --first-name "Jane" --last-name "Doe" --email "jane@example.com"
mesh contacts:create --first-name "Bob" --title "CEO" --organization "Acme Inc" --birthday "1990-05-15"
```

Update a contact:

```bash
mesh contacts:update --contact-id 12345 --title "CTO" --organization "NewCo"
mesh contacts:update --contact-id 12345 --email "new@example.com" --phone "+1234567890"
```

Archive / restore contacts:

```bash
mesh contacts:archive --contact-ids 12345
mesh contacts:restore --contact-ids 12345
```

Merge duplicate contacts:

```bash
mesh contacts:merge --contact-ids 12345 --contact-ids 67890
```

## Notes

List notes in a date range:

```bash
mesh notes --start "2025-01-01" --end "2025-12-31"
mesh notes --contact-ids 12345
```

Create a note on a contact:

```bash
mesh notes:create --contact-id 12345 --content "Met at the conference, very interested in partnerships."
mesh notes:create --contact-id 12345 --content "Follow up next week" --reminder-date "2026-03-01T09:00:00Z"
```

Notes support contact references in content: `[contact:123:John Doe]`.

## Groups

List all groups:

```bash
mesh groups
mesh groups --limit 50
```

Create a group:

```bash
mesh groups:create --title "Investors"
```

Update a group (rename, add/remove members):

```bash
mesh groups:update --group-id 42 --title "Angel Investors"
mesh groups:update --group-id 42 --add-contact-ids 12345 --add-contact-ids 67890
mesh groups:update --group-id 42 --remove-contact-ids 11111
```

## Events

List events in a date range:

```bash
mesh events --start "2025-01-01" --end "2025-03-01"
mesh events --contact-ids 12345
```

List upcoming events:

```bash
mesh events:upcoming
mesh events:upcoming --limit 20 --page 2
```

## Emails

List emails in a date range:

```bash
mesh emails --start "2025-01-01" --end "2025-02-01"
mesh emails --contact-ids 12345
```

List recent emails:

```bash
mesh emails:recent
mesh emails:recent --limit 25 --contact-ids 12345
```

## Reminders

List recent reminders:

```bash
mesh reminders:recent
mesh reminders:recent --limit 5
```

List upcoming reminders:

```bash
mesh reminders:upcoming
mesh reminders:upcoming --limit 20 --page 2
```

## Search Options Reference

The `contacts:search` command supports filters for:

- **Name**: `--name`
- **Work**: `--work-history-company`, `--work-history-position`, `--work-history-active`
- **Education**: `--education-history-school`, `--education-history-degree`, `--education-history-active`
- **Location**: `--location-latitude`, `--location-longitude`, `--location-distance`
- **Age**: `--age-gte`, `--age-lte`
- **Birthday**: `--upcoming-birthday-gte/lte`, `--previous-birthday-gte/lte`
- **Contact info**: `--information-type` (filter by type of info available)
- **Interaction dates**: `--first-email-date-gte/lte`, `--last-email-date-gte/lte`, `--first-event-date-gte/lte`, `--last-event-date-gte/lte`, `--first-text-message-date-gte/lte`, `--last-text-message-date-gte/lte`, `--first-interaction-date-gte/lte`, `--last-interaction-date-gte/lte`
- **Interaction counts**: `--email-count-gte/lte`, `--event-count-gte/lte`, `--text-message-count-gte/lte`
- **Notes**: `--note-content`, `--note-date-gte/lte`
- **Groups**: `--group-ids` (group ID or `"starred"`)
- **Integration**: `--integration`
- **Sorting**: `--sort-field`, `--sort-direction`
- **Pagination**: `--limit`, `--exclude-contact-ids`
- **Fields**: `--include-fields` (select which fields to return)
