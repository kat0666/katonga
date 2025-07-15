# Katonga

This repository contains a PowerShell script called `Install-ComfyUnleashed-OneShot.ps1`.
It provides an all-in-one installation of **ComfyUI**, the SDXL models and a set of
commonly used custom nodes. The script also sets up a local Python environment so
that everything is isolated in the folder of your choice.

## Requirements

- Windows with PowerShell and Git available in the `PATH`.
- Python **3.11**. The script checks for it and will attempt to install it via
  [winget](https://learn.microsoft.com/windows/package-manager/winget/) if not
  present.

## Running the installer

1. Open a PowerShell window.
2. Navigate to this repository's directory.
3. Execute the script:

   ```powershell
   Set-ExecutionPolicy -Scope Process Bypass
   ./Install-ComfyUnleashed-OneShot.ps1
   ```

By default everything will be installed into `E:\SDKAT\ComfyUI`. You can change
this location using the `-InstallDir` parameter when launching the script.

Once the installation finishes you will find a `launch_enhanced.bat` file inside
the selected directory. Running that batch file will start ComfyUI.

## Using the virtual environment

The installer creates a Python virtual environment in `venv` under the chosen
installation directory. To activate it manually:

```powershell
cd <InstallDir>
venv\Scripts\Activate.ps1
```

You can then install any extra dependencies required by additional custom nodes
with standard `pip` commands. For example, if a custom node provides a
`requirements.txt` file you may run:

```powershell
pip install -r custom_nodes\<NodeName>\requirements.txt
```

This keeps all packages contained within the installation folder.
