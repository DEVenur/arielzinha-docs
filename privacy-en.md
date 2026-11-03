# Arielzinha Privacy Policy

**Last updated:** November 3, 2026

## Summary

This policy explains what information Arielzinha processes, why it is used, and the limitations of its retention and deletion controls.

- **Identifiers:** Discord user, server, and channel IDs are used for commands, settings, and permissions.
- **Persisted data:** Server settings, user preferences, favorites, integrations, and Last.fm linking data may be stored.
- **Commands and messages:** The bot receives server messages to identify commands and mention-based song requests. This policy does not claim that all message history is archived; however, optional command logging can record command text or submitted options.
- **Third parties:** Operation may involve Discord, Last.fm, music providers, hosting, and infrastructure services.
- **Deletion:** The current code does not provide a public self-service mechanism to erase all data. Removing the bot from a server does not automatically delete records already stored.

## 1. Introduction

This Privacy Policy applies to **Arielzinha**, a music bot for Discord. It describes data processing performed by the implementation available in the [DEVenur/Arielzinha repository](https://github.com/DEVenur/Arielzinha).

Actual processing may vary depending on the instance configuration, particularly the database, command logging, technical logs, and enabled integrations.

## 2. Information processed

### 2.1. Discord identifiers and context

During operation, the bot uses identifiers such as:

- The ID of the user executing a command;
- Server (guild) and channel IDs;
- Context information needed to check permissions, roles, channels, and voice-channel presence.

The bot also queries member and voice-state information in real time to operate player features. The implementation uses this information during operation; this policy does not claim that a complete voice-presence history is stored.

### 2.2. Persisted user data

The implementation maintains records associated with user IDs that may include:

- Custom command prefix;
- Favorite links;
- Integration data;
- Tokens or integration credentials when used by related features;
- Recent track information or history;
- Last.fm username, session key, and scrobbling preference;
- Other auxiliary data required by bot features.

The Last.fm session key is an account-access credential and must be treated as sensitive authentication information.

### 2.3. Persisted server data

Records associated with servers may include:

- Server command prefix;
- Player and controller-channel settings;
- Skins and customizations;
- Roles and settings related to player usage;
- Voice-channel status and listen-along invites;
- Other preferences required by enabled features.

### 2.4. Queues, tracks, and auxiliary data

The bot can save playback queues associated with a user, including track metadata, creation date, and server ID. The implementation writes these queues to local files.

The scrobbling feature also maintains local auxiliary records for tracks that could not be identified or submitted to Last.fm. Local caches of metadata and query results are also used. These files should not be confused with a complete archive of all messages or all user activity.

### 2.5. Messages, commands, and logs

The bot receives server messages to recognize prefix commands, mentions, and song requests. This does not mean that every message is written to a database.

There are, however, diagnostic options:

- **COMMAND_LOG:** when enabled, it records executed commands, user and server identifiers, and, for prefix commands, the message content. For slash commands, it records the command name and filled options. This option is disabled by default in the example configuration.
- **ENABLE_LOGGER:** when enabled, it writes technical logs to `.logs/disnake.log`. The content depends on events and messages emitted by the libraries and the bot itself. This option is also disabled by default in the example configuration.
- **Process output:** diagnostic and error messages may be sent to standard output. The hosting platform may capture and retain this output under its own settings.

The reviewed code does not define a universal period that guarantees automatic deletion of all such records.

## 3. Purposes of processing

Data is used to:

- Execute commands and control music playback;
- Apply user and server settings, permissions, and preferences;
- Maintain favorites, saved queues, and customization features;
- Link Last.fm accounts and submit tracks when the user enables scrobbling;
- Maintain integrations and related features;
- Diagnose errors, monitor operation, and investigate abuse when the relevant logging features are enabled.

## 4. Third-party services and sharing

Use of the bot may involve:

- **Discord:** the platform through which the bot receives commands, identifiers, server context, and events required by its features.
- **Last.fm:** when configured, the bot uses the Last.fm API to authenticate the account, retrieve information, and submit track data for now playing and scrobbling. This may include artist name, track title, album, duration, and session key.
- **Music services:** depending on the source and feature used, queries and metadata may be processed by services such as Spotify, Deezer, and Lavalink servers configured for the instance.
- **Hosting and database providers:** data may be stored on the operator's local infrastructure or in MongoDB, depending on the instance configuration. Hosting and database providers may have technical access to data under their infrastructure.

We do not sell personal data. The instance operator should assess the third-party services actually enabled and their respective policies and terms.

**Last.fm technical note:** in the reviewed code version, requests to the Last.fm API use the HTTP endpoint `http://ws.audioscrobbler.com/2.0/`, not HTTPS. This means that this integration does not provide HTTPS transport encryption in this implementation. The operator should consider this risk before enabling the integration.

## 5. Storage and retention

The implementation supports local TinyMongo storage or MongoDB, depending on configuration. In addition, certain auxiliary data — including scrobble records, caches, and saved queues — is written to local files.

Storage duration depends on configuration, infrastructure, maintenance routines, and actions taken by the operator. The reviewed code does not establish a single retention period or guarantee automatic deletion of all data after a defined period.

Removing the bot from a server stops its operation in that server, but does not automatically remove existing records from the database, local files, backups, or hosting logs.

## 6. Security

The operator should protect database files, backups, environment variables, tokens, and session keys, restricting access to authorized people. Security also depends on the configuration and practices of the hosting and database providers.

This policy should not be interpreted as a guarantee of encryption at rest, encryption in transit across all services, or absolute security. In particular, the reviewed Last.fm integration uses HTTP, as described above.

## 7. Requests for access, correction, or deletion

The current code does not provide a public command that allows users to view, export, or fully delete all data associated with their account.

To request access, correction, or deletion, contact the operator through the [official Discord support server](https://dcserver.link/brasilpokedrink). Provide enough information to locate the records, but do not send passwords, tokens, or session keys.

Data removal may require actions in the database and instance files. Deletion of backups and records retained by the hosting provider also depends on that provider's policies and available controls. The bot does not implement an automatic completion deadline.

## 8. Children's privacy

Use of Arielzinha must comply with the age requirements applicable to Discord and the user's region. The operator must not allow use of the service in violation of those requirements.

## 9. Changes to this policy

This policy may be updated to reflect changes to the code, configuration, or services used. The current version will be published in this repository.

## 10. Contact

For questions or requests relating to data processed by an Arielzinha instance, use the [official Discord support server](https://dcserver.link/brasilpokedrink).
