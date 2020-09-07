# rofi-json

Simple [rofi](https://github.com/davatorium/rofi) external script that reads a json file and display the items as menu entries.

Supports icon.

## Usage

1. Make sure you have [jq](https://stedolan.github.io/jq/) (Command-line JSON processor) utility installed ([arch](https://www.archlinux.org/packages/community/x86_64/jq/) package).

2. Copy `rofi-json.sh` from this repo (or git clone and link) to your rofi's configuration folder (i.e. `~/.config/rofi`).

3. Create your JSON file (you can check examples folder).

4. Launch `rofi` with `-modi <NAME_OF_THE_MODE>:<PATH_OF_SCRIPT>/rofi-json.sh <JSON_FILE>`:

```bash
rofi -modi "My Apps":"~/.config/rofi/rofi-json.sh my_apps.json" -show "My Apps"
```

`<JSON_FILE>`: you can specify an absolute path (or ~), or just leave the json file name if it is located in the same directory as the `rofi-json.sh` file.

# JSON Example

```json
[
  {
    "name": "Google Chrome",
    "command": "google-chrome-stable",
    "icon": "google-chrome"
  },
  {
    "name": "gnome-disks"
  },
  {
    "name": "pavucontrol"
  },
  {
    "name": "journalctl -xeaf",
    "command": "urxvt -e bash -c 'journalctl -xeaf'"
  }
]
```

`command` key is optional. If not specified, the script will run `name`'s value.

`icon` key is optional (Default: `system-run`).

# Multiple JSON files

You can run rofi-json script with different json's files and create multiple modi's:

```bash
rofi \
    -modi config:"~/.config/rofi/rofi-json.sh config.json","My Apps":"~/.config/rofi/rofi-json.sh my_apps.json" \
    -show "My Apps"
```

## Credits

Adapted from [Myrmidon](https://github.com/moustacheful/myrmidon)
