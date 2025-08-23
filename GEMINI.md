## Project Overview

This project is a Photoshop plugin that seamlessly integrates with ComfyUI, a powerful AI image generation tool. It allows users to leverage ComfyUI's features directly within their Photoshop workflow.

The project consists of a Python backend and a JavaScript frontend (the Photoshop plugin). The backend, built with `aiohttp`, acts as a bridge, facilitating communication between Photoshop and ComfyUI via WebSockets. The frontend is a UXP-based Photoshop plugin that provides the user interface and interacts with the backend.

**Key Technologies:**

*   **Backend:** Python, `aiohttp`, `websockets`
*   **Frontend:** JavaScript (UXP for Photoshop plugins), Svelte, GSAP
*   **Dependencies:** `msgpack`, `aiofiles`, `GitPython`, `PyGithub`, `asyncio`, `numpy`

## Building and Running

The project doesn't have a traditional build process. The Python backend is a custom node for ComfyUI and runs as part of the ComfyUI server. The Photoshop plugin is installed separately.

**Running the Backend:**

1.  Ensure ComfyUI is installed.
2.  Place the `comfyui-photoshop` directory in the `ComfyUI/custom_nodes/` directory.
3.  Start the ComfyUI server. The backend will start automatically.

**Installing the Photoshop Plugin:**

The plugin can be installed in two ways:

1.  **Using the `.ccx` file:**
    *   Download the `.ccx` file from the `Install_Plugin` directory.
    *   Use a UXP installer like the "Adobe Extension Manager Command Line Tool" or "ZXP/UXP Installer" to install the plugin.
2.  **Using the installer script:**
    *   Run the `installer.py` script from the `Install_Plugin` directory:
        ```bash
        python Install_Plugin/installer.py
        ```
    *   The script will attempt to locate your Photoshop installation and copy the plugin files to the correct directory.

## Photoshop Plugin Internals

The Photoshop plugin is built using modern web technologies. The core of the plugin is located in the `Install_Plugin/3e6d64e0/assets` directory.

*   **`index-B_-tWO9a.js`**: This is the main JavaScript file for the plugin. It is a bundled Svelte application that has been processed by a bundler like Vite or Rollup. It contains all the UI components, application logic, and dependencies like GSAP and i18next for internationalization. The code is not minified and is human-readable.
*   **`index-C3nL6Ca2.css`**: This file contains all the styles for the plugin's UI. It uses CSS variables for theming and defines styles for different color schemes (light, dark, etc.).
*   **`defaultImg-BcFEYa9o.jpg`**: This is a default image used within the plugin.

The plugin uses a WebSocket connection to communicate with the Python backend. The `js/connection.js` file (which is likely bundled into the main `index.js` file) handles the WebSocket connection and message passing.

## Development Conventions

*   **Communication:** The frontend and backend communicate via a WebSocket connection. Messages are sent as JSON objects with a `type` and `data` field.
*   **File Structure:**
    *   `py/`: Contains the Python backend code.
    *   `js/`: Contains the JavaScript frontend code for the Photoshop plugin.
    *   `Install_Plugin/`: Contains the plugin installer and related files.
    *   `data/`: Contains workflows, preview files, and other data.
*   **Dependencies:** Python dependencies are listed in `pyproject.toml`. The frontend uses Svelte and GSAP, as indicated by the bundled JavaScript file.