# Apex Privacy Policy

**Last updated:** September 18, 2026

This Privacy Policy describes the information the current **Apex** source code stores and processes when Apex is used in Discord servers. It is based on the implementation currently in the project and may be updated when that implementation changes.

Apex is maintained by `lunnixzbw`.

## 1. Scope

Apex interacts with Discord data that is necessary for Discord bot operation and for the features enabled in a server. The exact information processed depends on which commands, modules, logging systems, and server configurations are used.

This policy distinguishes between information Apex stores, information stored because a feature is configured, and information processed temporarily while commands or event handlers run.

## 2. Information Stored Automatically

The current source code creates or updates some records as part of normal operation:

### Message-count tracking

For non-bot messages sent in servers, Apex can maintain a count associated with the sender's **Discord user ID** and the **Discord guild/server ID**. The implementation records a numeric count; it does not store the ordinary message text in this tracking table.

### Invite tracking

When invite tracking is used, Apex can store invite attribution data such as the **guild/server ID**, joining **member/user ID**, inviter **user ID**, invite code, and usage count. This allows Apex to identify and display invite activity.

Invite records may be adjusted or removed when members leave, according to the invite-tracking implementation.

## 3. Information Stored Because a Feature Is Enabled or Configured

Server administrators can configure features that cause Apex to store Discord IDs, settings, or user-provided information needed for those features. Examples in the current source include:

- **Server configuration:** guild IDs and configured channel, role, category, and message IDs for features such as Welcome/Farewell, JoinRole/AutoRole, Reaction Roles, Tickets, Join2Create, Logging, AutoReact, AutoBump, Autopost, Vanity Roles, feedback, media restrictions, and related systems.
- **Security configuration:** guild IDs, log-channel IDs, thresholds, time windows, punishment choices, module settings, whitelist entries, and user IDs used by Antinuke, AntiBetray, and AutoMod.
- **Moderation records:** guild IDs, moderator IDs, target IDs, usernames/tags, actions, reasons, channel IDs, and related moderation-log information.
- **User settings:** user/guild IDs and user-provided data used for AFK status, todos, reminders, profiles, playlists/favourites, and other personal server utilities.
- **Permissions and access controls:** user IDs, usernames, granting-user IDs, expiration information, and related settings for features such as no-prefix access, extra owners, delegated permissions, Premium access, blacklists, and ignore lists.
- **Giveaways and tickets:** user IDs, guild IDs, channel/message IDs, ticket or giveaway configuration, entries, hosts, prizes, status information, and related timestamps.

Apex stores these records because the relevant feature needs them to remember configuration, identify users/servers, perform automated actions, or display the requested information later.

## 4. Message Content and Other Temporary Processing

Apex does not treat all message processing as persistent storage. Some message-related data is read or held temporarily so that features can function.

### Commands and automation

Apex reads incoming message text when needed for prefix commands, hybrid commands, no-prefix handling, AutoMod checks, AutoReact triggers, AI-channel handling, AFK-related processing, and similar command/event logic.

### AutoMod

When AutoMod is enabled, Apex reads message content to check the configured modules, which can include spam, links, invites, bad words, mass mentions, capitalization, or ping-related conditions. The AutoMod configuration stores the selected settings and configured word list; ordinary message text is not automatically stored in the AutoMod configuration record.

### Message logging

If a server administrator enables and configures message logging, Apex can process and send deleted, edited, or bulk-deleted message information to the configured Discord logging channel. The logged information can include message content, author information, channel/server identifiers, and attachments.

### DM logging

The source contains an optional DM logging path. If the global `DM_LOGS` configuration is set to a logging destination, Apex can send messages received in direct messages to that configured logging destination, including message content and attachment links. The default source configuration leaves this logging destination unset.

### Snipe features

Snipe handling keeps a small, in-memory cache of recently deleted or edited messages for command functionality. The current implementation keeps up to the most recent ten deleted and ten edited entries per channel. This temporary cache can include content, user identifiers/display information, attachments, and timestamps. It is runtime memory rather than a database table.

### Temporary exports and cleanup files

Some dump/export and bulk-delete features create temporary files containing requested server or message data, send them as part of the command flow, and then attempt to remove the temporary file. These files are not intended to be a permanent data store.

## 5. AI and External API Processing

The current code uses external services for some features. Information included in a command may therefore be sent to the relevant provider when that feature is executed.

Examples verified in the source include:

- **AI chat:** user prompts and generated conversation data can be sent to Groq's API for AI responses. Apex also maintains AI history containing guild ID, channel ID, user ID, role, content, and timestamps for the configured AI history feature.
- **Text-to-speech:** text supplied to the TTS feature can be sent to Groq's audio API so audio can be generated.
- **Image generation:** the image-generation feature sends the user-provided prompt to the configured Bytez/model service.
- **Search/information commands:** search or lookup queries may be sent to external services such as Google/SerpAPI, YouTube, Wikipedia, GitHub, RSS/news services, and cryptocurrency data services.

The source contains an image-analysis command intended to send an image to an AI provider, but its current implementation references an undefined `config` variable before the external request is made. Accordingly, this policy does **not** treat successful external image transmission from that specific command as verified behaviour in the current source.

Third-party providers may process information under their own privacy policies and technical systems. Apex does not control how those external services independently process request or network data.

## 6. AI History Retention

The current AI history implementation automatically removes history older than **30 days**.

The source also includes functions for clearing a user's AI history and clearing a channel's AI history when those controls are invoked by the application.

## 7. Other Data Retention and Deletion

Apex does not currently implement one universal retention period for every database record or configuration file.

Different features have different cleanup behaviour. Some records are removed when a feature is reset, an entry is deleted, an activation expires, a member leaves, or another feature-specific cleanup path runs. Some configuration and user-created records can remain until the relevant feature is reset or the record is removed through its available command flow.

The current guild-leave event logs that Apex left a server; it does not provide a universal source-level routine that automatically purges every stored record belonging to that guild.

For questions about data associated with a server or user, contact the Apex support server and provide enough context to identify the relevant feature:

https://discord.gg/ezFVnB5eNB

## 8. Local Configuration and Runtime Files

The project also uses local files for some application state. Verified examples include embed-editor sessions/templates and operational application logs. Their contents depend on the feature that created them.

Embed-editor sessions contain identifiers and the current embed state and are scheduled to expire after approximately 24 hours. User-created embed templates are retained by the feature until they are changed or removed through the available workflow; the source does not define a universal expiration period for templates.

## 9. Information Apex Does Not Intentionally Collect as a Dedicated Feature

The current source code does not contain a dedicated collection feature for:

- IP addresses
- Email addresses
- Passwords
- Payment information
- Advertising profiles
- Standalone analytics or advertising tracking

This statement describes Apex's own implemented collection logic. Discord and external service providers may process technical, account, or network information independently under their own policies when you use their platforms or APIs.

## 10. Discord's Own Data Processing

Apex is a Discord application and depends on Discord's platform. Discord may separately collect and process information when you use Discord, join a server, interact with a bot, or access Discord-hosted content. That processing is governed by Discord's own terms and privacy policies, not this document.

## 11. Data Questions and Support

For privacy questions, requests concerning stored feature data, or help identifying which Apex feature is involved, use the official support server:

https://discord.gg/ezFVnB5eNB

Do not send bot tokens, API keys, passwords, or other credentials in a support request.

## 12. Changes to This Policy

This Privacy Policy may be updated when Apex's source code, storage behaviour, integrations, or features change.
