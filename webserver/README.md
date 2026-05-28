# WebMite HTTP server

A multi-page HTTP server for the Pico 2 W's WiFi, written in MMBasic. Serve a
small site straight off the SD card.

## Files

| File | Role |
|------|------|
| `server.bas` | The server. Run it to start serving. |
| `index.htm` | Home page (templated). |
| `status.htm` | Status page (templated). |
| `about.htm` | About page (templated). |
| `style.css` | Stylesheet, served raw as `text/css`. |
| `gpio.htm`, `files.htm` | Reference pages; the live `/gpio` and `/files` routes are generated dynamically by `server.bas`. |

## Routes

- `/` to `index.htm`
- `/status` to `status.htm`
- `/gpio` to a generated page showing live `MM.INFO$(PIN GPnn)` values
- `/files` to a generated full A: and B: drive listing
- `/about` to `about.htm`
- `/style.css` to `style.css`
- anything else to 404

## Setup

Copy all of these files to the SD card. Connect to WiFi (`OPTION WIFI ...`), then
one time from the prompt:

```basic
OPTION TCP SERVER PORT 80
```

Then run it:

```basic
RUN "B:server.bas"
```

It prints the server URL (`http://<ip>:80/`). Ctrl-C stops it.
