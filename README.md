# rice-hyperland-rahat5700

```bash
nano ~/.config/waybar/config.jsonc
```
```bash
[
    // TOP BAR
    {
        "name": "top-bar",
        "layer": "top",
        "position": "top",
        "height": 34,
        "modules-left": ["clock#time", "clock#date", "hyprland/workspaces"],
        "modules-right": ["tray", "pulseaudio", "network", "custom/poweroff"],
        "clock#time": {
            "format": "{:%H:%M}"
        },
        "clock#date": {
            "format": "{:%a %b %d}"
        },
        "hyprland/workspaces": {
            "format": "{icon}",
            "format-icons": {
                "active": "●",
                "default": "○"
            },
            "persistent-workspaces": {
                "*": 5
            },
            "on-click": "activate"
        },
        "custom/poweroff": {
            "format": "⏻",
            "on-click": "systemctl poweroff",
            "tooltip-format": "Power Off",
            "tooltip": true
        }
    },
    // LEFT BAR (Launcher)
    {
        "name": "left-bar",
        "layer": "top",
        "position": "left",
        "width": 55,
        "modules-left": ["wlr/taskbar"],
        "modules-right": ["custom/appmenu"],
        "wlr/taskbar": {
            "format": "{icon}",
            "icon-size": 28,
            "on-click": "activate"
        },
        "custom/appmenu": {
            "format": "",
            "on-click": "omarchy-menu app",
            "tooltip-format": "Application Menu",
            "tooltip": true
        }
    }
]
```

```bash
nano ~/.config/waybar/style.css
```

```bash
* {
    border: none;
    border-radius: 0;
    font-family: "Inter", "sans-serif";
    font-weight: 800; /* Bold like the image */
}

window#waybar {
    background-color: #1a1a1a; /* Pure dark charcoal */
    color: #ffffff;
}

#clock, #tray, #pulseaudio, #network, #custom-power {
    padding: 0 15px;
}

/* Vertical Launcher Styling */
#taskbar button {
    padding: 10px 0;
}

#taskbar button.active {
    background: rgba(255, 255, 255, 0.1);
    border-left: 3px solid #ffffff;
}
```
