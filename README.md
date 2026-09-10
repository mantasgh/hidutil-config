# hidutil config for macOS

Remaps the **Caps Lock** key to **F19** using macOS `hidutil`.

## Installation

1. Copy the `.plist` file to `~/Library/LaunchAgents`.

   ```bash
   curl -L --create-dirs \
           -o "$HOME/Library/LaunchAgents/com.local.KeyRemapping.plist" \
           "https://raw.githubusercontent.com/mantasgh/hidutil-config/main/com.local.KeyRemapping.plist"
   ```

2. Load the LaunchAgent.

   ```bash
   launchctl bootstrap \
           "gui/$(id -u)" \
           "$HOME/Library/LaunchAgents/com.local.KeyRemapping.plist"
   ```

   > `bootstrap` will fail if the LaunchAgent is already registered. In that case, reapply the mapping with:
   >
   > ```bash
   > launchctl kickstart "gui/$(id -u)/com.local.KeyRemapping"
   > ```

The remapping will be reapplied automatically whenever you log in.
