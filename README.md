# Eterea Obsidian Launcher - Modpack Creation Guide

https://etereagames.com/obsidianlauncher

This guide explains how to create, host, and update a custom modpack for the Eterea Obsidian Launcher using GitHub.

## 1. Local Files Preparation
1. Create a folder on your PC (e.g., `MyModpack`).
2. Inside it, create a subfolder named `mods`.
3. Place all the `.jar` mod files you want to use inside the `mods` folder.
4. (Optional) Test the mods with the standard Minecraft launcher to ensure there are no crashes or incompatibilities.

## 2. Creating the GitHub Repository
1. Go to [GitHub](https://github.com) and create a **New Repository**.
   - Name: e.g., `Updates-Server`
   - Visibility: **Public**
   - Initialize with a README (optional).
2. Take note of your username and the repository name.
   - Example: `Swonzo` / `Updates-Server`

## 3. Generating the Manifest
1. Open **Eterea Obsidian Launcher**.
2. Go to **Settings** (gear icon).
3. Scroll down to the **"Modpack Creator"** section.
4. Fill in the fields:
   - **Mods Source Folder:** The full path to your local `mods` folder on your PC.  
     *(Ex: `C:\Users\Swonzo\Desktop\MyModpack\mods`)*
   - **Base URL:** The "Raw" address where the files will be hosted on GitHub.  
     The format MUST be:  
     `https://raw.githubusercontent.com/<YOUR_NAME>/<YOUR_REPO>/main/mods`  
     *(Replace `<YOUR_NAME>` and `<YOUR_REPO>` with your actual details)*.
5. Click on **GENERATE MANIFEST.JSON**.
   - The launcher will create a `manifest.json` file inside your folder.

## 4. Uploading to GitHub
1. Upload the `mods` folder (containing the `.jar` files) and the `manifest.json` file to your GitHub repository.
   - You can use the GitHub web interface ("Upload files"), GitHub Desktop, or CLI.
   - Ensure the structure on GitHub looks like this:
     ```
     Updates-Server/
     ├── manifest.json
     └── mods/
         ├── mod1.jar
         ├── mod2.jar
         └── ...
     ```

## 5. Launcher Configuration (Client Side)
1. In the Launcher, on the main screen, click the `+` button next to "Servers".
2. Enter the name of the package.
3. In the URL field, enter the Raw link to the `manifest.json` file:
   `https://raw.githubusercontent.com/<YOUR_NAME>/<YOUR_REPO>/main/manifest.json`
4. Click the lightning bolt icon (⚡) to verify. If the version appears, click **Create**.

## 6. Updating the Modpack
When you want to add or remove mods:
1. Modify the files in your local `mods` folder.
2. Go back to the **Modpack Creator** in the launcher and click **GENERATE** again.
   - This will update the `manifest.json` with the new file hashes.
3. Upload the new files and the updated `manifest.json` to GitHub (Push).
4. Clients will automatically download the changes at the next launch.

---
**Troubleshooting**
- **Error "Unexpected token <":** You used the standard GitHub web page link instead of the Raw link. Ensure the URL starts with `raw.githubusercontent.com`.
- **Download failures:** You entered an incorrect "Base URL" during generation. Check that the links in the manifest correctly point to the `.jar` files.
