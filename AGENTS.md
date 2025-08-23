## Project Summary

This project is a Photoshop plugin that integrates with ComfyUI. It comprises a Python backend that runs as a ComfyUI custom node and a JavaScript-based UXP frontend that runs as a Photoshop plugin.

## Core Technologies

*   **Backend:** Python 3, `aiohttp`, `websockets`
*   **Frontend:** JavaScript, UXP (UXP is Adobe's modern extensibility technology for Creative Cloud applications), Svelte, GSAP
*   **Build Tools:** The frontend appears to be built using a modern JavaScript bundler like Vite or Rollup, but the build scripts are not included in the repository.

## File Structure

*   `py/`: Contains the Python backend source code.
*   `js/`: Contains the JavaScript source code for the Photoshop plugin.
*   `Install_Plugin/`: Contains the distributable Photoshop plugin, including the bundled JavaScript and CSS assets.
*   `data/`: Contains data files, such as ComfyUI workflows and preview images.
*   `pyproject.toml`: Defines the Python project dependencies.
*   `README.md`: The project's README file.
*   `GEMINI.md`: The instructional context file for the Gemini AI agent.

## Backend (Python)

The backend is a ComfyUI custom node that acts as a WebSocket server. It relays messages between the Photoshop plugin and the ComfyUI server.

*   **`py/Backend.py`**: The main backend file. It creates an `aiohttp` web server and handles WebSocket connections.
*   **`py/nodePlugin.py` and `py/nodeRemoteConnection.py`**: These files contain the ComfyUI node definitions.

**Running the Backend:**

1.  Ensure ComfyUI is installed.
2.  Place the `comfyui-photoshop` directory in the `ComfyUI/custom_nodes/` directory.
3.  Start the ComfyUI server.

## Frontend (JavaScript/UXP)

The frontend is a UXP-based Photoshop plugin. The source code is in the `js/` directory, and the bundled assets are in the `Install_Plugin/3e6d64e0/assets/` directory. This directory is the core of the Photoshop-side plugin.

*   **`js/main.js`**: The main entry point for the plugin.
*   **`js/connection.js`**: Handles the WebSocket connection to the backend.
*   **`Install_Plugin/3e6d64e0/assets/index-B_-tWO9a.js`**: This is the main JavaScript file for the plugin. It is a bundled Svelte application that has been processed by a bundler like Vite or Rollup. It contains all the UI components, application logic, and dependencies like GSAP and i18next for internationalization. The code is not minified and is human-readable.
*   **`Install_Plugin/3e6d64e0/assets/index-C3nL6Ca2.css`**: This file contains all the styles for the plugin. It uses CSS variables for theming and supports different color schemes.
*   **`Install_Plugin/3e6d64e0/assets/defaultImg-BcFEYa9o.jpg`**: A default image asset used in the plugin's UI.

**Installing the Frontend:**

1.  Run the `Install_Plugin/installer.py` script.
2.  Alternatively, install the `Install_Plugin/3e6d64e0_PS.ccx` file using a UXP installer.

## Development

To make changes to the backend, edit the Python files in the `py/` directory and restart the ComfyUI server.

To make changes to the frontend, you would need to set up a development environment for UXP and Svelte. The build scripts are not included in the repository, so you would need to create them. The general workflow would be:

1.  Modify the JavaScript files in the `js/` directory.
2.  Bundle the JavaScript and CSS files using a tool like Vite or Rollup.
3.  Copy the bundled assets to the `Install_Plugin/3e6d64e0/assets/` directory.
4.  Reload the plugin in Photoshop.