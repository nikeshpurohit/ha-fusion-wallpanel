# ha-fusion-wallpanel

A modern, easy-to-use and performant custom [Home Assistant](https://www.home-assistant.io/) dashboard

This is a revived project (mostly for personal use) forked from the amazing [ha-fusion](https://github.com/matt8707/ha-fusion) project. The aim of this is to optimise ha-fusion for use with small lower resolution devices such as common wall tablets. The intention is to stay in sync with the original project with a slightly more active development strategy. 

### Help Wanted!
I am no expert in TypeScript or svelte, so contributions are welcome!

## Screenshots

![](image.png)


## Roadmap

   - Get Available alarm control panel modes from hass and display in alarm control panel modal
   - Add selection of arm modes to alarm control panel modal
   - Reduce the size of colour picker on smaller viewports to avoid scrolling
   - Media player card
   - Graph card in main area
   - Audio support for cameras
   - Scale camera stream to viewport
   - Allow iframe as view content

   - ONVIF Two way audio for compatible cameras (fully kiosk browser)


---

## 📣 Pre-beta

The current state of this project is **pre-beta**. This means that there's basic functionality missing, incomplete features and unresolved issues. General feedback, bug reports and feature requests are welcome!



---


## Installation

Addon is currently not yet available. Check back soon!

### Add-on

For "Operating System" or "Supervised" installation methods, you can install ha-fusion as an add-on:

1. **Add Repository**: To begin, add the ha-fusion add-on repository to your Home Assistant instance. Click the button below or manually add the repository using this URL: <https://github.com/nikeshpurohit/addon-ha-fusion-wallpanel>.

   [![Open your Home Assistant instance and show the add add-on repository dialog with a specific repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fnikeshpurohit%2Faddon-ha-fusion-wallpanel)

2. **Install Add-on**: After adding the repository, refresh the add-on store page. Locate ha-fusion in the list and proceed with the installation.

---

### Docker

If you're using the "Container" or "Core" installation methods, ha-fusion can be installed via Docker:

1. **Docker Compose File**: Place your edited copy of the [docker-compose.yml](https://github.com/nikeshpurohit/ha-fusion/blob/main/docker-compose.yml) file in a suitable directory.

2. **Create Container**:
   Run the following commands in your terminal to start the container:

   ```bash
   cd path/to/docker-compose.yml
   docker-compose up -d ha-fusion-wallpanel
   ```

#### Update

To update to the latest version of ha-fusion, run the following commands:

```bash
docker-compose pull ha-fusion
docker-compose up -d ha-fusion
```

<details>
<summary>
   <b>Other</b>
</summary>

Without docker-compose, updating the container involves additional steps. For each update, it's necessary to first stop the current container, remove it, pull the new image, and then execute the docker run command again.

```bash
docker run -d \
  --name ha-fusion \
  --network bridge \
  -p 5050:5050 \
  -v /path/to/ha-fusion:/app/data \
  -e TZ=Europe/Stockholm \
  -e HASS_URL=http://192.168.1.241:8123 \
  --restart always \
  ghcr.io/nikeshpurohit/ha-fusion-wallpanel
```

#### Kubernetes

If you prefer to use Kubernetes, see [Chart README.md](https://github.com/matt8707/ha-fusion/tree/167c320918544416e2f9272e1edad64b7329269a/charts/ha-fusion)

</details>

...

---

## Query strings

These will only function if you have exposed a port in the add-on configuration or by using Docker. Note that when using Ingress, query strings cannot be read.

### View

To set a particular view when the page loads, add the "view" parameter. For example, if you have a "Bedroom" view, append the query string `?view=Bedroom` to the URL.

### Menu

To disable the menu button, append the query string `?menu=false` to the URL. This is useful when you want to avoid unwanted changes to your dashboard, such as on wall-mounted tablets.

---

## Keyboard Shortcuts

| Key                 | Description |
| ------------------- | ----------- |
| **f**               | filter      |
| **esc**             | exit        |
| **cmd + s**         | save        |
| **cmd + z**         | undo        |
| **cmd + shift + z** | redo        |

---

## Debug

To debug any errors, check the "Log" tab if you're using the addon, or use `docker logs ha-fusion` for Docker setups. To inspect frontend issues, open the browser's console.

---

## Develop

To begin contributing to the project, you'll first need to install node. It's also recommended to install pnpm. If you're unfamiliar with Svelte, consider doing the tutorial at <https://learn.svelte.dev>

```bash
# prerequisites (macos)
brew install node pnpm

# install
git clone https://github.com/nikeshpurohit/ha-fusion-wallpanel.git
cd ha-fusion
pnpm install

# environment
cp .env.example .env
code .env

# server
npm run dev -- --open

# dependencies
pnpm outdated
pnpm update

# lint
npm run check
npm run lint
npm run format
```
