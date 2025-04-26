# Torn Modular Bot - User Guide

This guide explains how to use the Torn Modular Bot and its various features within your Discord server.

## For All Users

These commands are available to everyone in the server where the bot is active.

### 1. Adding Your API Key

The bot needs your Torn API key to fetch your data for verification, travel monitoring, and other features. Your key is stored securely (encrypted).

* **Command:** `/mykey add`
* **Action:** Opens a pop-up form (modal) where you can securely paste your 16-character Torn API key.
* **How to get a key:** Create one on Torn: [https://www.torn.com/preferences.php#tab=api](https://www.torn.com/preferences.php#tab=api) (Requires enabling `Public status`, `Profile information`, and `Faction tree` access for full functionality).
* **Note:** You only need to do this once per server where you use the bot.

### 2. Removing Your API Key

If you no longer want the bot to use your key in this specific server:

* **Command:** `/mykey remove`
* **Action:** Removes your stored API key for this server from the bot's database.

### 3. Verifying Your Torn Account

Verification links your Discord account to your Torn account within the bot, enabling features like automatic nickname updates and role assignments based on your Torn faction.

* **Prerequisite:** Ensure your Discord account is linked on your Torn profile: [https://www.torn.com/discord](https://www.torn.com/discord)
* **Command:** `/verify`
* **Action:** The bot checks the Torn API using your Discord ID to find your linked Torn account. If successful, it updates your verification status in the database and may update your nickname and roles according to server settings.

### 4. Re-verifying Your Account

If your Torn name, faction, or linked Discord account changes, you might need to re-verify.

* **Command:** `/reverify`
* **Action:** Re-runs the verification check using your Discord ID.

### 5. Setting Up DM Travel Alerts

Get Direct Messages when specific monitored players or faction members travel to or arrive from certain countries.

* **Command:** `/dmalert`
* **Action:** Opens an interactive menu:
    1.  **Select Source:** Choose the Faction or individually Monitored Player you want alerts for.
    2.  **Select Countries:** Choose the specific destination countries you care about, or select "Monitor ALL Countries".
    3.  **Save/Update:** Saves your preferences for the selected source.
    4.  **Remove Alert:** Removes the DM alert setting for the currently selected source.
    5.  **Cancel:** Closes the menu without saving changes.
* **Note:** You can configure different country settings for each monitored faction or player.

## For Server Administrators (and Bot Owner)

These commands require Administrator permissions in the Discord server (or being the Bot Owner).

### Managing Monitored Factions

* **Add Faction:** `/faction add`
    * Opens a pop-up to enter the Torn Faction ID to start monitoring.
* **Remove Faction:** `/faction remove [faction: Faction ID or Name]`
    * Stops monitoring the specified faction and cleans up related settings (like DM alerts and list message IDs).
* **List Factions:** `/faction list`
    * Shows all factions currently monitored in the server and their configured notification settings.
* **Configure Faction Settings:** `/faction settings [faction: Faction ID or Name]`
    * Opens a menu to select which feature to configure for the chosen faction (Hospital Notifications, Revive List, Travel Notifications/List, Hospital List).
    * Each selection opens a sub-menu to set the specific channel and/or role for that feature for that faction. Setting a channel to `None` (by selecting no channel) disables that specific feature for the faction.

### Managing Monitored Players (Individual)

* **Add Player:** `/player add [player_id: Torn Player ID]`
    * Starts monitoring an individual player (useful for players not in monitored factions or for specific tracking).
* **Remove Player:** `/player remove [player_id: Torn Player ID]`
    * Stops monitoring the specified individual player.
* **List Players:** `/player list`
    * Shows all individually monitored players and their notification channels.
* **Set Player Channel:** `/player set_channel [player: Player ID or Name]`
    * Opens a menu to set a specific notification channel for travel/hospital alerts for an individually monitored player (overrides faction settings for this player). Select `None` to disable channel notifications for them.

### Managing Verification Roles

* **Add Faction Role:** `/factionrole add [faction_id: Torn Faction ID] [role: Discord Role]`
    * Maps a Torn Faction ID to a specific Discord role. Verified members of this faction will automatically receive this role.
* **Remove Faction Role:** `/factionrole remove [faction_id: Faction ID (optional)] [role: Discord Role (optional)]`
    * Removes a mapping. Specify *either* the Faction ID *or* the Discord Role to remove its association.
* **List Faction Roles:** `/factionrole list`
    * Shows all current Faction ID -> Discord Role mappings.

### Managing Global Settings

* **Toggle Features:**
    * `/settings toggle_hospital [enabled: True/False]`
    * `/settings toggle_revive_list [enabled: True/False]`
    * `/settings toggle_travel [enabled: True/False]`
    * Globally enables or disables the core functionality of these modules for the entire server.
* **Set Hospital Ping Times:** `/settings set_hospital_ping_times`
    * Opens a pop-up to enter comma-separated minutes (e.g., `10, 2`) before hospital exit when notifications should be sent. Leave blank to disable timed pings.
* **Set Travel Check Interval:** `/settings set_travel_interval [interval: Seconds]`
    * Sets how often (in seconds, min 30) the bot checks the API for travel updates. Lower values mean faster updates but higher API key usage.
* **Set Travel Message Auto-Delete:** `/settings set_travel_message_delay [minutes: 0-60]`
    * Sets how long (in minutes) travel notification messages remain in channels before being automatically deleted by the bot. Set to `0` to disable auto-deletion.
* **Show All Settings:** `/settings show`
    * Displays an embed summarizing all the current global settings and toggle statuses.

### Admin Verification Tools

* **Verify All Members:** `/verifyall`
    * Initiates a check of *all* members in the server. It attempts to verify unverified members, updates details for already verified members, and removes verification/resets details for members whose Torn link is broken or mismatched. This can take time in large servers.
* **Re-verify Member (Context Menu):** Right-click (or tap-hold on mobile) on a user -> Apps -> Reverify Torn User
    * Forces a re-verification check for a specific user, updating their details.

### Payment Status

* **Check Status:** `/payment status`
    * Shows if the bot's subscription for this server is active and when it expires. Also displays instructions on how to subscribe/extend.
* **View History:** `/payment history`
    * Shows a list of the most recent payments or overrides applied to this server's subscription.
---

If you encounter issues or have questions, please contact the server administrators or the bot owner.
