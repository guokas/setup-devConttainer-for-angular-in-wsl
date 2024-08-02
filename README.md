![angular_setup_dev_container](https://github.com/user-attachments/assets/3c035a6a-2065-4bb9-b07e-d3a7fe11dbcd)



# Install Ubuntu OS for WSL
```powershell
# PowerShell
wsl --install Ubuntu

wsl -l -v

wsl --shutdown
```

# Install Docker Engine
https://docs.docker.com/engine/install/ubuntu/
follow the instructions to install Docker Engine.

```sh
sudo docker run hello-world
```

## Add to docker user group

```
sudo groupadd docker
sudo usermod -aG docker $USER
```

# Configure Dev Container

Install `Dev Containers` and `WSL` extensions in Visual Studio Code.

Press F1, choose "Add Dev Container Configuration Files" command to configure DevContainer.

```sh
ng --version
```

Specify Forward ports `"forwardPorts": [4200]` and network mode `--network=host`

```sh
wsl:~$ cat .devcontainer/devcontainer.json

// For format details, see https://aka.ms/devcontainer.json. For config options, see the
// README at: https://github.com/devcontainers/templates/tree/main/src/typescript-node
{
        "name": "Node.js & TypeScript",
        // Or use a Dockerfile or Docker Compose file. More info: https://containers.dev/guide/dockerfile
        "image": "mcr.microsoft.com/devcontainers/typescript-node:1-22-bookworm",
        "features": {
                "ghcr.io/devcontainers-contrib/features/angular-cli:2": {}
        }

        // Features to add to the dev container. More info: https://containers.dev/features.
        // "features": {},

        // Use 'forwardPorts' to make a list of ports inside the container available locally.
        ,"forwardPorts": [4200]
        ,"runArgs": [
                "--network=host"
        ]
        // Use 'postCreateCommand' to run commands after the container is created.
        // "postCreateCommand": "yarn install",

        // Configure tool-specific properties.
        // "customizations": {},

        // Uncomment to connect as root instead. More info: https://aka.ms/dev-containers-non-root.


```

# create project

```sh
ng create angular-dev-container-project

cd angular-dev-container-project
```

Then `ng serve` with default port `4200` for serving. 



