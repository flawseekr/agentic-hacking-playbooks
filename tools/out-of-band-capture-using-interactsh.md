---
name: out-of-band-capture-using-interactsh
description: Capture and verify out-of-band (OOB) interactions using interactsh-client.
---

## Prerequisites

1. Check whether the Interactsh client binary is installed and accessible:

   ```bash
   interactsh-client -h
   ```

2. If the command executes successfully and displays the help output, proceed to the [Usage](#usage) section.

3. If the binary is missing or the command is not found, follow the [Installation](#installation) instructions before proceeding.

4. Verify the installation by running `interactsh-client -h` again. Ensure the help output is displayed successfully before continuing.

## Installation

1. Visit the `https://github.com/projectdiscovery/interactsh/releases/latest` page.
2. Download the binary that matches the target operating system and architecture.
3. Move the downloaded binary to the user's local binary directory:
   - **Linux:** `~/.local/bin/`
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

## Usage

1. Start the Interactsh client in the background using the following command:

   ```bash
   interactsh-client \
     -sf ~/.local/share/interactsh/session.yaml \
     -o /tmp/interactsh-interactions.jsonl \
     -json \
     > /dev/null 2>&1 &
   ```

2. Capture the generated OOB hostname from the client output. Use this hostname as the callback domain in your test payloads.

3. Trigger the OOB interaction by sending the appropriate payload to the target application.

4. Verify whether the target generated an interaction by inspecting the log file:

   ```bash
   cat /tmp/interactsh-interactions.jsonl
   ```

5. Review the recorded interactions and correlate them with your test payloads to determine whether an OOB callback occurred.

6. Once testing is complete, terminate the background Interactsh client process to stop monitoring.

**Note:** Keep the Interactsh client running throughout the testing process. An empty interaction log does not establish that a vulnerability is absent; it only indicates that no interaction was recorded during the observation period.
