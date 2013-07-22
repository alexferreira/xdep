# xdep

npm package to deploy node.js apps.


## Usage

1. Install globally with npm:

```
sudo npm install -g xdep
```

2. Make sure these properties exist in your `deploy.json`:

```json
{
  "name": "your app name",
  "appDir": "your dir app name",
  "repository": {
    "url": "your repository address",
    "type": "git"
  },
  "defaultDeploy": "chokmah",
  "defaultBranch": "master",
  "config": {
    "commands": {
      "monitor": "tail -f log/*.log"
    },
    "targets": {
      "development": {
        "ssh": {
          "user": "username of server",
          "port": 22,
          "hosts": [
            "ip address of your server"
          ]
        },
        "env": {
          "HOST": "0.0.0.0",
          "PORT": 3000,
          "NODE_ENV": "production"
        }
      },
      "production": {
        "ssh": {
          "user": "username of server",
          "port": 22,
          "hosts": [
            "ip address of your server"
          ]
        },
        "env": {
          "HOST": "0.0.0.0",
          "PORT": 3000,
          "NODE_ENV": "production"
        }
      }
    }
  }
}
```

3. Use the CLI to deploy your code like a boss:

```
Usage: xdep [command]

Available commands:

    list    list available deploy targets
    init    <target> - prepares target to accept deployments
    start   <target> - starts the remote server
    stop    <target> - stops the remote server
    diff    <target> [--branch branch] - display what will be deployed on target
    deploy  <target> [--branch branch] - deploy code
    abort   <target> - aborts a hanging deploy
    monitor <target> - tail logs on target
    exec    <target> - output environment variables for target
```
