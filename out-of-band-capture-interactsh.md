## Installation

1. Visit the `https://github.com/projectdiscovery/interactsh/releases/latest` page.
2. Download the binary that matches the target operating system and architecture.
3. Move the downloaded binary to the user's local binary directory:
   - **Linux:** `~/.local/bin/`
   - **Windows:** `%LOCALAPPDATA%\Programs\` or another directory included in the user's `PATH`.
4. On Linux, grant executable permission to the binary:
   ```bash
   chmod +x ~/.local/bin/interactsh-client
   ```
5. Verify that the binary is accessible and executable by running:
   ```bash
   interactsh-client -h
   ```
6. Confirm that the help output is displayed successfully. If the command is not found, verify that the installation directory is included in the system's `PATH`.

**Important:** Use the correct binary filename provided in the release archive. The official CLI executable is generally named `interactsh-client`.
