# NagramY

A fork of Nagram X with enhanced configuration management and streamlined release workflows.

### Configuration Management

- Configuration file: [`TMessagesProj/src/main/java/tw/nekomimi/nekogram/NagramXConfig.java`](TMessagesProj/src/main/java/tw/nekomimi/nekogram/NagramXConfig.java)
- Uses vanilla Android keys:
  - API ID: `6`
  - API Hash: `eb06d4abfb49dc3eeb1aeb98ae0f581e`

### GitHub Actions Setup

To enable automated builds and releases:

1. **Fork the repository** and go to Settings → Secrets and variables → Actions

2. **Configure build properties**
   Create a `keys/local.properties` file with:

   ```
   KEYSTORE_PASS=your_keystore_password
   ALIAS_NAME=your_key_alias
   ALIAS_PASS=your_alias_password
   TELEGRAM_APP_ID=6
   TELEGRAM_APP_HASH=eb06d4abfb49dc3eeb1aeb98ae0f581e
   ```

3. **Encode your local.properties:**

   ```bash
   base64 -w 0 keys/local.properties
   ```

4. **Add required secrets:**

   - `HELPER_BOT_TOKEN` - Your Telegram bot token
   - `LOCAL_PROPERTIES` - Base64 encoded local.properties content
   - `CHANNEL_MAIN` - Telegram channel ID for main releases
   - `CHANNEL_CANARY` - Telegram channel ID for canary builds
   - `CHANNEL_DEV` - Telegram channel ID for dev builds

5. **Push to trigger builds:**
   - Push to `main` → Production release
   - Push to `canary` → Beta release
   - Push to `dev` → Debug release

---

# Nagram X

A variant of [Nagram](https://github.com/NextAlone/Nagram) with additional features.

## Download

You can grab the latest versions in these two ways:

*   **CI Channel:** [https://t.me/NagramX](https://t.me/NagramX)
*   **GitHub Actions Artifacts:**  You can also download artifacts from the [GitHub Actions](https://github.com/risin42/NagramX/actions/workflows/staging.yml) page

## NagramX Changes
- **Additional Features**
  - AI Translator
  - AI Transcription
  - Hide the Premium and Help sections in settings
  - Hide side share button
  - Avoids requesting camera permission when selecting images
  - Ask before sending bot command
  - Ask before opening inline links
  - Translate Entire Chats
  - Center title in chats
  - Custom drawer elements
  - Remove Archived Chats from dialog list
  - Use icons instead of "deleted"/"edited"
  - Save attachments by chat name
  - Send messages silently by default
  - Use folder name as title
  - Spring Animations
  - Disable message background color and emojis
  - Custom chat name
  - Hide Reactions
  - Hide gift button
  - Hide dividers
  - Solar icons
  - Tab style (Default, Pure, Pills)
  - Admin shortcuts in chats
  - Left button action (NoQuote forward, Reply, Save, Direct Share)
  - And more ?

----
> [!NOTE]
> Some changes of Nagram and NekoX have been removed

----
<details>
<summary><strong>Nagram Changes</strong></summary>

1. Nice icon (thanks to MaitungTM)
2. Combine message
3. Editable text style
4. Forced copy
5. Invert reply
6. Quick reply in longClick menu (thanks to @blxueya)
7. Undo and Redo
8. Scrollable chat preview (thanks to TeleTux)
9. Noise suppress and voice enhance
</details>

----
<details>
<summary><strong>NekoX Changes</strong></summary>

- Most of Nekogram's features
- Unlimited login accounts
- **Proxy**
  - Built-in VMess, Shadowsocks, SSR, Trojan-GFW proxies support (No longer maintained)
  - Built-in public proxy (WebSocket relay via Cloudflare CDN)
  - Proxy subscription support
  - Ipv6 MTProxy support
  - Able to parse all proxy subscription format: SIP008, ssr, v2rayN, vmess1, shit ios app formats, clash config and more
  - Proxies import and export, remarks, speed measurement, sorting, delete unusable nodes, etc
  - Scan the QR code (any link, can add a proxy)
  - The ( vmess / vmess1 / ss / ssr / trojan ) proxy link in the message can be clicked
  - Allow auto-disabling proxy when VPN is enabled
  - Proxy automatic switcher
  - Don't alert "Proxy unavailable" for non-current account
- **Stickers**
  - Custom
  - Add stickers without sticker pack
  - Sticker set list backup / restore / share
- **Internationalization**
  - OpenCC Chinese Convert
  - Full InstantView translation support
  - Translation support for selected text on input and in messages
  - Google Cloud Translate / Yandex.Translate support
  - Force English emoji keywords to be loaded
  - Persian calendar support
- **Additional Options**
  - Option to disable vibration
  - Dialog sorting is optional "Unread and can be prioritized for reminding" etc
  - Option to skip "regret within five seconds"
  - Option to not send comment first when forwarding
  - Option to use nekox chat input menu: replace record button with a menu which contains an switch to control link preview (enabled by default)
  - Option to disable link preview by default: to prevent the server from knowing that the link is shared through Telegram.
  - Option to ignore Android-only content restrictions (except for the Play Store version).
  - Custom cache directory (supports external storage)
  - Custom server (official, test DC)
  - Option to block others from starting a secret chat with you
  - Option to disable trending
- **Additional Actions**
  - Allow clicking on links in self profile
  - Delete all messages in group
  - Unblock all users support
  - Login via QR code
  - Scan and confirm the login QR code directly
  - Allow clearing app data
  - Proxies, groups, channels, sticker packs are able to be shared as QR codes
  - Add "@Name" when long-pressing @user option
  - Allow creating a group without inviting anyone
  - Allow upgrading a group to a supergroup
  - Mark dialogs as read using tab menu
  - Enabled set auto delete timer option for private chats and private groups
  - Support saving multiple selected messages to Saved Messages
  - Support unpinning multiple selected messages
  - View stats option for messages
- **Optimization**
  - Keep the original file name when downloading files
  - View the data center you belong to when you don't have an avatar
  - Enhanced notification service, optional version without Google Services
  - Improved session dialog
  - Improved link long click menu
  - Improved hide messages from blocked users feature
  - Don't process cleanup draft events after opening chat
- **Others**
  - OpenKeychain client (sign / verify / decrypt / import)
  - Text replacer
- **UI**
  - Telegram X style menu for unpinning messages
  - Built-in Material Design themes / Telegram X style icons
- And more :)
</details>

----
## Compilation Guide

1. Obtain API credentials (`TELEGRAM_APP_ID` and `TELEGRAM_APP_HASH`) from [Telegram Developer Portal](https://my.telegram.org/auth). Create `local.properties` in the project root with:

   ```properties
   TELEGRAM_APP_ID=<your_telegram_app_id>
   TELEGRAM_APP_HASH=<your_telegram_app_hash>
   ```

2. For APK signing: Replace `release.keystore` with your keystore and add signing configuration to `local.properties`:

   ```properties
   KEYSTORE_PASS=<your_keystore_password>
   ALIAS_NAME=<your_alias_name>
   ALIAS_PASS=<your_alias_password>
   ```

3. For FCM support: Replace `TMessagesProj/google-services.json` with your own configuration file.

4. Open the project in Android Studio to start building.

## GitHub Actions Build

1. Replace `TMessagesProj/release.keystore` with your keystore file.

2. Configure `local.properties` with the following:

   ```properties
   KEYSTORE_PASS=<your_keystore_password>
   ALIAS_NAME=<your_alias_name>
   ALIAS_PASS=<your_alias_password>
   TELEGRAM_APP_ID=<your_telegram_app_id>
   TELEGRAM_APP_HASH=<your_telegram_app_hash>
   ```

   Base64 encode the contents of this file.

3. Configure GitHub Action secrets:
   - `LOCAL_PROPERTIES`: Base64-encoded content from step 2
   - `HELPER_BOT_TOKEN`: Telegram bot token from [@Botfather](https://t.me/Botfather) (e.g., `1111:abcd`)
   - `HELPER_BOT_TARGET`: Primary Telegram chat ID (e.g., `777000`)
   - `HELPER_BOT_CANARY_TARGET`: Chat ID for test builds and metadata (can match `HELPER_BOT_TARGET`)

4. Trigger the Release Build workflow.

## Acknowledgments

- [AyuGram](https://github.com/AyuGram/AyuGram4A)
- [Cherrygram](https://github.com/arsLan4k1390/Cherrygram)
- [Dr4iv3rNope](https://github.com/Dr4iv3rNope/NotSoAndroidAyuGram)
- [exteraGram](https://github.com/exteraSquad/exteraGram)
- [Nagram](https://github.com/NextAlone/Nagram)
- [Nekogram](https://github.com/Nekogram/Nekogram)
- [OctoGram](https://github.com/OctoGramApp/OctoGram)
