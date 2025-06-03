# GitHub Runner Configuration and Troubleshooting Guide

## Overview
A dedicated GitHub Runner operates as a standalone service on the current testnet hub, responsible for executing all GitHub Actions and their associated build processes.

## Access and Authentication
To troubleshoot the Runner service, establish a connection to the hub using either SSH or NodeShell protocols.
![image](https://github.com/user-attachments/assets/03de6c68-3cd9-4d1e-8901-8328444d7154)

## User Context Switch
After successful authentication, switch to the designated "runner" user account to access the appropriate runtime environment.

## Directory Structure
The runner's home directory contains an "actions-runner" folder, which serves as the execution environment for all build operations. The runner user maintains connectivity to the server's Docker daemon to facilitate containerized build processes.

## Service Management
Launch the runner process within a screen session to ensure persistent operation. Execute the runner using the following command:

```bash
cd ~/actions-runner
screen -S github-runner
./run.sh
```
Expected Output:

√ Connected to GitHub
Current runner version: '2.324.0'
2025-06-03 10:13:49Z: Listening for Jobs

/home/runner/
└── actions-runner/
    ├── run.sh
    ├── _diag/
    └── [other runner files]

## Troubleshooting
Comprehensive logs for troubleshooting purposes are maintained in the _diag/ directory within the actions-runner folder.
```bash
ls -la ~/actions-runner/_diag/
tail -f ~/actions-runner/_diag/Runner_*.log
```

## Notes
All build steps are executed from the runner user context
The runner connects to the Docker daemon running on the server



![hydra-github-action drawio](https://github.com/user-attachments/assets/f9291eed-ad66-4383-b7b3-2687e259d06b)
