# CONFIG.md — User Configuration
# Populated by the onboarding skill.
# Agents read this to know how this PAP instance is configured.

---

## Identity

AGENT_NAME=
USER_PREFERRED_NAME=
TIMEZONE=
LOCALE=

---

## Operating mode

PAP_MODE=
# 1 = dedicated clean machine (recommended)
# 2 = daily machine (limited security)

CLEAN_MACHINE_OS=
# macOS or Windows

---

## Discord configuration

DISCORD_SERVER_ID=
DISCORD_BOT_TOKEN_VAULT_REFERENCE=
# Token stored in PAP Vault — this is just the reference key

DISCORD_CHANNELS_CREATED=false
# Set to true after onboarding completes channel setup

---

## Output destination

OUTPUT_DESTINATION=
# google_drive or onedrive

OUTPUT_DRIVE_PREFERENCE=
# platform_only | personal_allowed | choose_per_workspace

OUTPUT_ACCOUNT_EMAIL=
# The platform account email, not personal

---

## Authorized capabilities

COMPUTER_USE_AUTHORIZED=
# true | false | not_yet_asked

COMPUTER_USE_TRUST_LEVEL=
# global_authorized | per_domain | ask_each_time | not_authorized

CLAUDE_IN_CHROME_AUTHORIZED=
# true | false

CHROME_INSTALLED=
# true | false

TAILSCALE_CONFIGURED=
# true | false | not_yet_asked

---

## Password manager

PASSWORD_MANAGER=
# 1password | bitwarden | keepassxc | other | none

CREDENTIAL_ACCESS_LEVEL=
# full = MCP integration with PAP Vault
# keychain = system keychain only
# none = no automated credential access

---

## Active connectors
# Updated as connectors are authorized
# Format: CONNECTOR_[NAME]=true|false|[access_level]

CONNECTOR_GOOGLE_DRIVE=
CONNECTOR_GOOGLE_CALENDAR=
CONNECTOR_GMAIL=
CONNECTOR_ONEDRIVE=
CONNECTOR_OUTLOOK_CALENDAR=
CONNECTOR_OUTLOOK_EMAIL=
CONNECTOR_SLACK=
CONNECTOR_NOTION=
CONNECTOR_TASK_MANAGER=

---

## User preferences

COMMUNICATION_STYLE=
# brief | conversational | detailed

RESPONSE_LENGTH=
# short | medium | long

INFORMATION_STYLE=
# data | visual | reading | interactive | mix

DISPLAY_MODE=
# light | dark | system

COLOR_PRIMARY=
COLOR_ACCENT_1=
COLOR_ACCENT_2=

DATE_FORMAT=
# MM/DD/YYYY | DD/MM/YYYY | YYYY-MM-DD

TIME_FORMAT=
# 12h | 24h

WEEK_STARTS_ON=
# monday | sunday

WORKING_STYLE_ACTIVE_HOURS=
# early_morning | daytime | evening | night | varies

PROACTIVE_OUTREACH=
# often | sometimes | rarely

---

## Trust levels per action category

TRUST_LEVEL_CALENDAR_READ=
TRUST_LEVEL_CALENDAR_WRITE=
TRUST_LEVEL_EMAIL_READ=
TRUST_LEVEL_EMAIL_DRAFT=
TRUST_LEVEL_DRIVE_READ_PLATFORM=
TRUST_LEVEL_DRIVE_WRITE_PLATFORM=
TRUST_LEVEL_DRIVE_READ_PERSONAL=
# silent | act_and_notify | explicit_required
# (purchases are always explicit_required — not configurable)

---

## Cost preferences

USAGE_WARNING_THRESHOLD=
# 70 | 85 | 95 (percentage)

USAGE_REPORTING_FREQUENCY=
# weekly | monthly | only_when_high

COST_OPTIMIZATION_PREFERENCE=
# show_each | auto_small | significant_only

---

## Improvement preferences

IMPROVEMENTS_FREQUENCY=
# as_they_come | weekly | only_significant | never

IMPROVEMENTS_MAX_SURFACED=
# 1 | 3 | 5 | all
# (only shown if IMPROVEMENTS_FREQUENCY != never)

---

## UI preferences

EMOJI_IN_CHANNEL_NAMES=
# yes_suggest | only_if_asked | never

NOTIFICATION_QUIET_HOURS_START=
NOTIFICATION_QUIET_HOURS_END=
# 24-hour format, e.g. 22:00 and 07:00

---

## GitHub backup

GITHUB_USERNAME=
GITHUB_BACKUP_REPO=
# e.g., "platform-config"

GITHUB_TOKEN_VAULT_REFERENCE=
# Token stored in PAP Vault

BACKUP_SCHEDULE=23:00
# Default: 11pm user timezone

LAST_BACKUP_TIMESTAMP=
LAST_BACKUP_STATUS=
# success | failed | partial

---

## PAP plugin metadata

PAP_VERSION_INSTALLED=1.0.0
PAP_INSTALLED_DATE=
LAST_UPDATE_CHECK=
LAST_UPDATE_APPLIED=

ONBOARDING_COMPLETED=false
ONBOARDING_STEP=
ONBOARDING_COMPLETED_DATE=
ASSUMPTIONS_EXPLAINED=false

---

## Active workspaces
# Updated by scaffolder as workspaces are created
# WORKSPACE: [name]
#   STATUS: designing | live | paused | archived
#   CREATED: [date]
#   CHANNEL: #[channel-name]
#   DRIVE: [path or "pending"]
#   LAST_RUN: [timestamp]
#   NEXT_RUN: [timestamp]

---

## System health flags

CLAUDE_DESKTOP_AUTOLAUNCH_CONFIGURED=
QMD_RUNNING=
QMD_INDEX_HEALTHY=
LAST_VALIDATOR_RUN=
LAST_STEWARD_RUN=
NEVER_SLEEP_CONFIGURED=
