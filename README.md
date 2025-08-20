# `niri-run-or-raise.sh`

A _run-or-raise-style_ helper script to focus, cycle, or launch an application
window with the [Niri](https://github.com/YaLTeR/niri) Wayland window manager.

## Features

- If the app is _not running_, it launches ("runs") a new instance.
- If the app is _running but not focused_, it focuses ("raises") the app window.
- If the app is _running, focused, and has multiple instances_, it cycles
  through the different instances.

## Requirements

- `niri`
- `bash`
- `jq`
- `notify-send`

## Installation

First clone the repository to a location of your choosing, _e.g._ `~/opt`.

```bash
git clone git@github.com:fasterius/niri-run-or-raise.git ~/opt/niri-run-or-raise
```

## Usage

```bash
niri-run-or-raise.sh [APP_CLASS] [APP_CMD]
```

- `APP_CLASS` (required): The application's ID (_e.g._ `firefox`).
- `APP_CMD` (optional): Command to run the application (_e.g._ `firefox`).

If you're not sure what ID a particular app has you can run `niri msg windows`
or `niri msg -j windows | jq` and look it up.

## Examples

You'd normally want to bind the script to a key binding in your Niri config,
like so:

```kdl
Super+F { spawn "~/opt/niri-run-or-raise.sh" "firefox"; }
```

Some apps might have more complicated launch commands, such as Flatpaks, in
which case you can supply them as well:

```kdl
Super+F { spawn "~/opt/niri-run-or-raise.sh" "spotify" "flatpak run com.spotify.Client"; }
```
