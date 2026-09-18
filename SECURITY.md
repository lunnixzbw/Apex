# Apex Security Policy

**Last updated:** September 18, 2026

This document explains the security limitations of Apex and how to report suspected security issues.

## Security Limitations

### Discord Permissions

Apex can only perform actions that Discord allows for the bot in the relevant server, channel, or member context. Missing permissions can prevent moderation, role, channel, logging, or other administrative actions from succeeding.

### Role Hierarchy

Discord role hierarchy limits which members Apex can manage. If a target member's highest role is equal to or above Apex's highest role, Apex may be unable to remove roles, kick, ban, or otherwise manage that member.

### Bot and API Limitations

Apex depends on Discord's API and, for selected features, external APIs. Rate limits, outages, permission changes, malformed data, network failures, API changes, or third-party service problems can affect functionality.

### Required Permissions

Server administrators should grant only the permissions needed for the features they intend to use. Security and moderation systems cannot take actions that Discord does not permit.

### Antinuke, AntiBetray, and AutoMod Limitations

Apex's security systems rely on the events, thresholds, time windows, module settings, whitelists, permissions, and API responses available to the application. They are designed to automate defensive responses, but they cannot guarantee detection or prevention of every malicious action.

Security controls should therefore be used alongside careful permissions, secure administrator accounts, and human oversight.

## Reporting a Vulnerability

Security issues should be reported privately through the official Apex support server:

https://discord.gg/ezFVnB5eNB

When possible, include:

- A clear description of the issue.
- Steps needed to reproduce it.
- The affected command, event, or feature.
- Relevant screenshots or logs, when appropriate and safe to share.
- The expected behaviour and the actual behaviour.
- Relevant Apex or project version information, when known.

Please provide enough detail for the issue to be investigated, but do not include secrets or unnecessary private data.

## Responsible Disclosure

Please avoid publicly posting exploit details, proof-of-concept material that enables abuse, or other sensitive information before Apex has had a reasonable opportunity to investigate the report.

Never expose or paste the following into public channels or support requests:

- Bot tokens
- API keys
- Passwords or other credentials
- Private user information
- Sensitive server information

Apex does not operate a bug bounty program unless one is explicitly announced separately.

## Scope of This Policy

This security policy describes the current Apex application's security limitations and reporting process. It does not promise that every reported issue will result in a code change, a fixed deadline, public disclosure, or any particular outcome.
