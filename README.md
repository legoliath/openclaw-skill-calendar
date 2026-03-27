# 📅 OpenClaw Skill: Apple Calendar CLI (accli) - Manage your macOS calendar from the command line.

![OpenClaw Skill](https://img.shields.io/badge/OpenClaw-Skill-blue) ![Status](https://img.shields.io/badge/Status-Active-green)

## Overview
The `accli` skill provides a powerful command-line interface for interacting with Apple Calendar on macOS. It enables comprehensive calendar management, including listing calendars, querying events, creating, updating, and deleting events, and checking free/busy availability. This skill is designed for programmatic access and automation of calendar-related tasks, leveraging JavaScript for Automation (JXA) on macOS.

## Features
- List all available calendars by name and ID.
- Query events with flexible filtering by date range, keywords, and maximum results.
- Retrieve details for specific events by ID.
- Create new timed or all-day events with customizable summaries, start/end times, locations, and descriptions.
- Update existing event details.
- Delete events (with user confirmation).
- Check free/busy time slots across multiple calendars.
- Configure a default calendar for streamlined usage.
- JSON output support for easy parsing and integration with other tools.

## Installation
The `accli` tool is a Node.js package.
> [!IMPORTANT]
> This skill requires macOS as it utilizes JavaScript for Automation (JXA).

```bash
npm install -g @joargp/accli
```

## Usage
The `accli` skill provides various commands for calendar interaction. Always prefer `--json` for programmatic parsing and `--calendar-id` for reliability.

**Common Commands:**

| Command                 | Description                                                                  | Example                                                                                                                                                                                                                                                                                                              |
| :---------------------- | :--------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `accli calendars`       | List all available calendars.                                                | `accli calendars --json`                                                                                                                                                                                                                                                                                             |
| `accli events`          | List events for a specific calendar.                                         | `accli events Work --from $(date +%Y-%m-%d) --to $(date -v+1d +%Y-%m-%d) --json` (View today's schedule)                                                                                                                                                                                                        |
| `accli create`          | Create a new event.                                                          | `accli create Work --summary "Team Standup" --start 2025-01-15T09:00 --end 2025-01-15T09:30 --json`                                                                                                                                                                                                                   |
| `accli update`          | Update an existing event by ID.                                              | `accli update Work event-id-123 --summary "Updated Meeting Title" --start 2025-01-15T15:00 --end 2025-01-15T16:00 --json`                                                                                                                                                                                          |
| `accli delete`          | Delete an event by ID.                                                       | `accli delete Work event-id-123 --json`                                                                                                                                                                                                                                                                              |
| `accli freebusy`        | Check free/busy slots across calendars.                                      | `accli freebusy --calendar Work --calendar Personal --from 2025-01-15T09:00 --to 2025-01-15T18:00 --json`                                                                                                                                                                                                          |

> [!TIP]
> For detailed options and examples for each command, refer to the `SKILL.md` file or run `accli <command> --help`.

## Configuration
The `accli` tool allows you to set and manage a default calendar, which is useful for simplifying commands by omitting the calendar name.

| Command             | Description                                   |
| :------------------ | :-------------------------------------------- |
| `accli config set-default` | Interactively set a default calendar. |
| `accli config set-default --calendar <name>` | Set a default calendar by name. |
| `accli config show` | Display the current configuration.            |
| `accli config clear` | Clear the default calendar setting.           |

## File Structure
```
/Users/charlesM/.openclaw/workspace/skills/accli/
├── SKILL.md      # Detailed documentation and usage guide for the OpenClaw skill.
└── _meta.json    # Metadata file for the OpenClaw skill.
```
