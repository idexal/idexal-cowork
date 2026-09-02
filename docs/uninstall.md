# Uninstall idexal CoWork

There are two ways to uninstall idexal CoWork depending on whether you want to keep local data.

## Option 1: Uninstall app/binaries only (keep database)

This removes installed application files and CLI/package artifacts while keeping workspace, settings, and task data for later restore.

### macOS app (manual drag-installed build)

```bash
pkill -f '/Applications/idexal CoWork.app' || true
rm -rf "/Applications/idexal CoWork.app"
```

### npm global package install

```bash
npm uninstall -g idexal-cowork
```

### Local install in a folder

```bash
rm -rf ~/cowork-run
```

### Source/development clone

```bash
rm -rf /path/to/idexal-cowork
```

### Packaged Linux server release

```bash
sudo systemctl stop idexal-cowork-node
sudo systemctl disable idexal-cowork-node
sudo rm -f /etc/systemd/system/idexal-cowork-node.service
sudo systemctl daemon-reload
sudo rm -rf /opt/idexal-cowork
```

### VPS/headless Docker install

```bash
cd /path/to/docker-compose-dir
docker compose down
```

### VPS/headless systemd install

```bash
sudo systemctl stop idexal-cowork idexal-cowork-node
sudo systemctl disable idexal-cowork idexal-cowork-node
sudo rm -f /etc/systemd/system/idexal-cowork.service
sudo rm -f /etc/systemd/system/idexal-cowork-node.service
sudo systemctl daemon-reload
```

### Data locations to keep

Choose the one used by your install:

- macOS (Electron): `~/Library/Application Support/idexal/`
- Linux desktop/Electron: `~/.config/idexal/`
- Linux daemon/headless fallback: `~/.cowork/`
- Node daemon custom path: value passed in `COWORK_USER_DATA_DIR` or `--user-data-dir`
- Packaged/systemd example paths: `/var/lib/idexal-cowork`, `/srv/cowork/workspace`, and any custom path in `/etc/idexal-cowork.env`
- Docker example paths: named volume `cowork_data`, named volume `cowork_workspace`, and any host bind mount in `/workspace`

## Option 2: Full uninstall + data deletion (database included) — irrecoverable

> **WARNING:** This removes all application data and settings (tasks, tasks timeline, memory, credentials, channel/session state, and the local database). **All data will be deleted and everything will be gone forever.**

Use this only when you are sure you want to destroy local state.

### Delete all user-data locations

```bash
rm -rf ~/Library/Application\ Support/idexal-cowork
rm -rf ~/.config/idexal-cowork
rm -rf ~/.cowork
```

### Remove with custom user-data path

```bash
rm -rf "$COWORK_USER_DATA_DIR"
```

### Fully remove Docker install data

```bash
cd /path/to/docker-compose-dir
docker compose down -v
docker compose rm -f
```

### Fully remove systemd/headless example data

```bash
sudo rm -rf /var/lib/idexal-cowork
sudo rm -rf /srv/cowork/workspace
```

After the data wipe, also remove remaining app binaries/shell package entries from Option 1 if you haven't already.
