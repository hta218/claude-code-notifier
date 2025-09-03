# Claude Code Notification

📢 Send system notifications when Claude Code requests permissions or completes tasks

A cross-platform notification script that integrates with Claude Code to show system notifications for various events like session completions and permission requests.

## Installation

### Step 1: Install terminal-notifier (macOS only)
```bash
brew install terminal-notifier
```

### Step 2: Create the script file
```bash
curl -o ~/.claude/claude-notification.sh https://raw.githubusercontent.com/hta218/claude-notification/main/claude-notification.sh
```

### Step 3: Make it executable (macOS/Linux)
```bash
chmod +x ~/.claude/claude-notification.sh
```
**Note**: Windows users can skip this step.

### Step 4: Enable notifications on your system
Make sure notifications are enabled for Terminal/your shell application in your system settings.

![Enable Terminal Notifications](https://cdn.shopify.com/s/files/1/0669/0262/2504/files/terminal-notifier.png?v=1756888696)

### Step 5: Add configuration to Claude settings
Create or edit `~/.claude/settings.json` and add:
```json
{
  "hooks": {
    "Notification": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "~/.claude/claude-notification.sh"
          }
        ]
      }
    ],
    "Stop": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "~/.claude/claude-notification.sh"
          }
        ]
      }
    ],
    "SessionEnd": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "~/.claude/claude-notification.sh"
          }
        ]
      }
    ]
  }
}
```

### Step 6: Restart Claude Code
Restart Claude Code to apply the changes then simply prompt 'Hello' to see notifications in action.

## Usage

Once installed, the script will automatically trigger notifications with default System sounds when Claude Code:
- Requests permissions or user input (Notification hook)
- Completes tasks or responses (Stop hook)
- Ends sessions (SessionEnd hook)

![Notification Preview](https://cdn.shopify.com/s/files/1/0669/0262/2504/files/terminal-notifier-noties.png?v=1756889242)

## Event Types

The script handles different notification types:

- **SessionEnd**: Shows "Session completed ✅"
- **Stop**: Shows "Response finished 🏁"  
- **Notification**: Shows the original message from Claude
- **Other events**: Shows the event name with the message

## Requirements

### macOS (recommended)
- [`terminal-notifier`](https://github.com/julienXX/terminal-notifier) for pushing notifications
- [`jq`](https://github.com/jqlang/jq) for JSON processing
- Install: `brew install terminal-notifier jq`

### Linux
- `notify-send` (usually pre-installed)
- Install if missing: `sudo apt install libnotify-bin`

### Windows
- PowerShell (built-in on modern Windows)
- Uses Windows Toast notifications

## Customization

You can modify the script to:
- Change notification messages
- Add different sounds
- Log notifications to a file (uncomment the last line)
- Customize notification appearance

## Contributing

Feel free to submit issues and pull requests to improve the script!