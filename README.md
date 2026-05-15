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
        "modules-left": ["clock#time", "clock#date"],
        "modules-right": ["tray", "pulseaudio", "network", "custom/power"],

        "clock#time": {
            "format": "{:%H:%M   %H:%M}"
        },
        "clock#date": {
            "format": "{:%a %b %d}"
        },
        "custom/power": {
            "format": "⏻",
            "on-click": "omarchy-menu power", // Uses Omarchy's built-in power menu
            "tooltip": false
        }
    },

    // LEFT BAR (Launcher)
    {
        "name": "left-bar",
        "layer": "top",
        "position": "left",
        "width": 55,
        "modules-left": ["wlr/taskbar"],

        "wlr/taskbar": {
            "format": "{icon}",
            "icon-size": 28,
            "on-click": "activate"
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
