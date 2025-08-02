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

Latest versions are available through:
* [Telegram Channel](https://t.me/NagramX) (Latest Beta)
* [GitHub Actions](https://github.com/risin42/NagramX/actions/workflows/staging.yml) (CI Artifacts)
* [GitHub Releases](https://github.com/risin42/NagramX/releases) (Latest Stable)

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
