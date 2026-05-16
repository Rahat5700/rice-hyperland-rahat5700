# rice-hyperland-rahat5700
```bash
pkill waybar && omarchy-waybar &
```

```bash
nano ~/.config/waybar/config.jsonc
```
```bash

[
  {
    "name": "top-bar",
    "reload_style_on_change": true,
    "layer": "top",
    "position": "top",
    "height": 26,
    "spacing": 0,
    "modules-left": [
      "clock"
    ],
    "modules-center": [],
    "modules-right": [
      "custom/weather",
      "custom/update",
      "custom/voxtype",
      "custom/screenrecording-indicator",
      "custom/idle-indicator",
      "custom/notification-silencing-indicator",
      "hyprland/workspaces",
      "group/tray-expander",
      "bluetooth",
      "network",
      "pulseaudio",
      "cpu",
      "battery"
    ],
    "hyprland/workspaces": {
      "on-click": "activate",
      "format": "{icon}",
      "format-icons": {
        "default": "\uea71",
        "1": "1",
        "2": "2",
        "3": "3",
        "4": "4",
        "5": "5",
        "6": "6",
        "7": "7",
        "8": "8",
        "9": "9",
        "10": "0",
        "active": "\udb85\udcfb"
      },
      "persistent-workspaces": {
        "1": [],
        "2": [],
        "3": [],
        "4": [],
        "5": []
      }
    },
    "custom/omarchy": {
      "format": "<span font='omarchy'>\ue900</span>",
      "on-click": "omarchy-menu",
      "on-click-right": "xdg-terminal-exec",
      "tooltip-format": "Omarchy Menu\n\nSuper + Alt + Space"
    },
    "custom/update": {
      "format": "\uf021",
      "exec": "omarchy-update-available",
      "on-click": "omarchy-launch-floating-terminal-with-presentation omarchy-update",
      "tooltip-format": "Omarchy update available",
      "signal": 7,
      "interval": 21600
    },
    "cpu": {
      "interval": 5,
      "format": "\udb80\udf5b",
      "on-click": "omarchy-launch-or-focus-tui btop",
      "on-click-right": "alacritty"
    },
    "clock": {
      "format": "{:L%A %H:%M}",
      "format-alt": "{:L%d %B W%V %Y}",
      "tooltip": false,
      "on-click-right": "omarchy-launch-floating-terminal-with-presentation omarchy-tz-select"
    },
    "custom/weather": {
      "exec": "$OMARCHY_PATH/default/waybar/weather.sh",
      "return-type": "json",
      "interval": 60,
      "tooltip": false,
      "on-click": "notify-send -u low \"$(omarchy-weather-status)\""
    },
    "network": {
      "format-icons": [
        "\udb82\udd2f",
        "\udb82\udd1f",
        "\udb82\udd22",
        "\udb82\udd25",
        "\udb82\udd28"
      ],
      "format": "{icon}",
      "format-wifi": "{icon}",
      "format-ethernet": "\udb80\udc02",
      "format-disconnected": "\udb82\udd2e",
      "tooltip-format-wifi": "{essid} ({frequency} GHz)",
      "tooltip-format-ethernet": "Connected",
      "tooltip-format-disconnected": "Disconnected",
      "interval": 3,
      "spacing": 1,
      "on-click": "omarchy-launch-wifi"
    },
    "battery": {
      "format": "{capacity}% {icon}",
      "format-discharging": "{icon}",
      "format-charging": "{icon}",
      "format-plugged": "\uf1e6",
      "format-icons": {
        "charging": [
          "\udb82\udc9c",
          "\udb80\udc86",
          "\udb80\udc87",
          "\udb80\udc88",
          "\udb82\udc9d",
          "\udb80\udc89",
          "\udb82\udc9e",
          "\udb80\udc8a",
          "\udb80\udc8b",
          "\udb80\udc85"
        ],
        "default": [
          "\udb80\udc7a",
          "\udb80\udc7b",
          "\udb80\udc7c",
          "\udb80\udc7d",
          "\udb80\udc7e",
          "\udb80\udc7f",
          "\udb80\udc80",
          "\udb80\udc81",
          "\udb80\udc82",
          "\udb80\udc79"
        ]
      },
      "format-full": "\udb80\udc85",
      "tooltip-format-discharging": "{power:>1.0f}W\u2193 {capacity}%",
      "tooltip-format-charging": "{power:>1.0f}W\u2191 {capacity}%",
      "interval": 5,
      "on-click": "omarchy-menu power",
      "on-click-right": "notify-send -u low \"$(omarchy-battery-status)\"",
      "states": {
        "warning": 20,
        "critical": 10
      }
    },
    "bluetooth": {
      "format": "\uf294",
      "format-off": "\udb80\udcb2",
      "format-disabled": "\udb80\udcb2",
      "format-connected": "\udb80\udcb1",
      "format-no-controller": "",
      "tooltip-format": "Devices connected: {num_connections}",
      "on-click": "omarchy-launch-bluetooth"
    },
    "pulseaudio": {
      "format": "{icon}",
      "on-click": "omarchy-launch-audio",
      "on-click-right": "pamixer -t",
      "tooltip-format": "Playing at {volume}%",
      "scroll-step": 5,
      "format-muted": "\ueee8",
      "format-icons": {
        "headphone": "\uf025",
        "headset": "\uf025",
        "default": [
          "\uf026",
          "\uf027",
          "\uf028"
        ]
      }
    },
    "group/tray-expander": {
      "orientation": "inherit",
      "drawer": {
        "transition-duration": 600,
        "children-class": "tray-group-item"
      },
      "modules": [
        "custom/expand-icon",
        "tray"
      ]
    },
    "custom/expand-icon": {
      "format": "\uf053",
      "tooltip": false,
      "on-scroll-up": "",
      "on-scroll-down": "",
      "on-scroll-left": "",
      "on-scroll-right": ""
    },
    "custom/screenrecording-indicator": {
      "on-click": "omarchy-capture-screenrecording",
      "exec": "$OMARCHY_PATH/default/waybar/indicators/screen-recording.sh",
      "signal": 8,
      "return-type": "json"
    },
    "custom/idle-indicator": {
      "on-click": "omarchy-toggle-idle",
      "exec": "$OMARCHY_PATH/default/waybar/indicators/idle.sh",
      "signal": 9,
      "return-type": "json"
    },
    "custom/notification-silencing-indicator": {
      "on-click": "omarchy-toggle-notification-silencing",
      "exec": "$OMARCHY_PATH/default/waybar/indicators/notification-silencing.sh",
      "signal": 10,
      "return-type": "json"
    },
    "custom/voxtype": {
      "exec": "omarchy-voxtype-status",
      "return-type": "json",
      "format": "{icon}",
      "format-icons": {
        "idle": "",
        "recording": "\udb80\udf6c",
        "transcribing": "\udb81\udd1f"
      },
      "tooltip": true,
      "on-click-right": "omarchy-voxtype-config",
      "on-click": "omarchy-voxtype-model"
    },
    "tray": {
      "icon-size": 12,
      "spacing": 17
    }
  },
  {
    "name": "left-bar",
    "layer": "top",
    "position": "left",
    "width": 26,
    "spacing": 0,
    "modules-left": [
      "custom/omarchy-app1",
      "custom/omarchy-app2",
      "custom/omarchy-app3",
      "custom/omarchy-app4",
      "custom/omarchy-app5",
      "wlr/taskbar"
    ],
    "modules-right": [
      "custom/omarchy"
    ],
    "wlr/taskbar": {
      "format": "{icon}",
      "icon-size": 18,
      "on-click": "activate"
    },
    "custom/omarchy-app1": {
      "format": "󰣆",
      "on-click": "omarchy-launch-wifi",
      "tooltip-format": "Omarchy Network Connection"
    },
    "custom/omarchy-app2": {
      "format": "󰀻",
      "on-click": "omarchy-launch-bluetooth",
      "tooltip-format": "Omarchy Bluetooth Settings"
    },
    "custom/omarchy-app3": {
      "format": "󰠮",
      "on-click": "omarchy-launch-audio",
      "tooltip-format": "Omarchy Audio Controller"
    },
    "custom/omarchy-app4": {
      "format": "󰎆",
      "on-click": "omarchy-launch-floating-terminal-with-presentation omarchy-tz-select",
      "tooltip-format": "Omarchy Timezone Select"
    },
    "custom/omarchy-app5": {
      "format": "󰙯",
      "on-click": "omarchy-launch-floating-terminal-with-presentation omarchy-update",
      "tooltip-format": "Omarchy System Updates"
    },
    "custom/omarchy": {
      "format": "<span font='omarchy'>\ue900</span>",
      "on-click": "omarchy-menu",
      "on-click-right": "xdg-terminal-exec",
      "tooltip-format": "Omarchy Menu\n\nSuper + Alt + Space"
    }
  }
]
```
```bash
nano ~/.config/waybar/style.css
```

```bash
@import "../omarchy/current/theme/waybar.css";

* {
  background-color: @background;
  color: @foreground;

  border: none;
  border-radius: 0;
  min-height: 0;
  font-family: 'JetBrainsMono Nerd Font';
  font-size: 12px;
}

.modules-left {
  margin-left: 8px;
}

.modules-right {
  margin-right: 8px;
}

#workspaces button {
  all: initial;
  padding: 0 6px;
  margin: 0 1.5px;
  min-width: 9px;
}

#workspaces button.empty {
  opacity: 0.5;
}

#cpu,
#battery,
#pulseaudio,
#custom-omarchy,
#custom-update {
  min-width: 12px;
  margin: 0 7.5px;
}

#tray {
  margin-right: 16px;
}

#bluetooth {
  margin-right: 17px;
}

#network {
  margin-right: 13px;
}

#custom-expand-icon {
  margin-right: 18px;
}

tooltip {
  padding: 2px;
}

#custom-update {
  font-size: 10px;
}

#clock {
  margin-left: 8.75px;
}

#custom-weather {
  margin-left: 7.5px;
  margin-right: 7.5px;
}

#custom-weather.unavailable {
  min-width: 0;
  margin: 0;
  padding: 0;
}

.hidden {
  opacity: 0;
}

#custom-screenrecording-indicator,
#custom-idle-indicator,
#custom-notification-silencing-indicator {
  min-width: 12px;
  margin-left: 5px;
  margin-right: 0;
  font-size: 10px;
  padding-bottom: 1px;
}

#custom-screenrecording-indicator.active {
  color: #a55555;
}

#custom-idle-indicator.active,
#custom-notification-silencing-indicator.active {
  color: #a55555;
}

#custom-voxtype {
  min-width: 12px;
  margin: 0 0 0 7.5px;
}

#custom-voxtype.recording {
  color: #a55555;
}

/* --- Left Bar Centering Refinements --- */
window#waybar.left {
    border-right: 1px solid rgba(255, 255, 255, 0.1);
}

/* Force all modules in the left bar to center and ignore global horizontal margins */
window#waybar.left .modules-left,
window#waybar.left .modules-center,
window#waybar.left .modules-right {
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: column;
    align-items: center; /* Center horizontally in the vertical stack */
}

/* Specific module centering in the left bar */
window#waybar.left #custom-omarchy-app1,
window#waybar.left #custom-omarchy-app2,
window#waybar.left #custom-omarchy-app3,
window#waybar.left #custom-omarchy-app4,
window#waybar.left #custom-omarchy-app5,
window#waybar.left #taskbar,
window#waybar.left #custom-omarchy {
    margin-left: 0;
    margin-right: 0;
    margin-top: 5px;
    margin-bottom: 5px;
    padding: 0;
    min-width: 26px; /* Fill the bar width */
    text-align: center;
}

/* Ensure icons inside custom modules are centered */
window#waybar.left label {
    margin: 0 auto;
}

/* Taskbar Button Alignment */
#taskbar button {
    padding: 4px 0;
    margin: 2px 0;
    min-width: 26px;
}

/* Launcher at the very bottom */
#custom-omarchy {
    margin-bottom: 8px;
    font-size: 14px;
}

/* App Icons styling */
#custom-omarchy-app1, 
#custom-omarchy-app2, 
#custom-omarchy-app3, 
#custom-omarchy-app4, 
#custom-omarchy-app5 {
    font-size: 16px;
    color: @foreground;
}

/* Top Bar Spacing */
#clock {
    margin-left: 12px;
}

#custom-weather {
    margin-left: 8px;
}
```
