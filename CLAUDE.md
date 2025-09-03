# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Structure

This is a minimal project directory containing:
- `test.js` - A simple JavaScript test file
- `claude-notification.sh` - System notification hook script for Claude Code events
- `.claude/settings.json` - Claude Code configuration with notification hooks

## Claude Code Configuration

The repository has Claude Code hooks configured for notifications:
- **Notification Hook**: Triggers system notifications using `claude-notification.sh`
- **Stop Hook**: Shows completion notifications when responses finish

The notification script supports cross-platform notifications (macOS, Linux, Windows) and can be customized for different hook events like SessionEnd, Stop, and general Notifications.

## Development Commands

Since this is a minimal JavaScript project without package.json or build configuration, standard Node.js commands apply:
- `node test.js` - Run the test file
- `node <filename>.js` - Execute any JavaScript file

No specific build, lint, or test commands are configured in this repository.