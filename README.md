# Claude Code Notification

🔔 Get desktop notifications when Claude Code needs permission or finishes stuff

A cross-platform notification script that integrates with Claude Code to show system notifications for various events like session completions and permission requests.

## Installation

1. Create the notification script in your Claude directory:
   ```bash
   # Create the script file
   curl -o ~/.claude/claude-notification.sh https://raw.githubusercontent.com/hta218/claude-notification/main/claude-notification.sh
   
   # Make it executable (macOS/Linux)
   chmod +x ~/.claude/claude-notification.sh
   ```
   
   **Note**: Windows users can skip the `chmod` step as it's not needed.

2. Add hook configuration to your Claude settings:
   ```bash
   # Create or update ~/.claude/settings.json
   cat > ~/.claude/settings.json << 'EOF'
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
       ]
     }
   }
   EOF
   ```

3. Restart Claude Code to apply the changes

## Usage

Once installed, the script will automatically trigger notifications when Claude Code:
- Requests permissions or user input
- Completes tasks or responses
- Ends sessions

## Event Types

The script handles different notification types:

- **SessionEnd**: Shows "Session completed ✅"
- **Stop**: Shows "Response finished 🏁"  
- **Notification**: Shows the original message from Claude
- **Other events**: Shows the event name with the message

## Requirements

### macOS
- `terminal-notifier` (recommended) or built-in `osascript`
- Install terminal-notifier: `brew install terminal-notifier`

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