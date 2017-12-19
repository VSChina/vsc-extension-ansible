[![Travis CI](https://travis-ci.org/VSChina/vscode-ansible.svg?branch=master)](https://travis-ci.org/VSChina/vscode-ansible)
[![AppVeyor](https://ci.appveyor.com/api/projects/status/kq11m16pl22k29un?svg=true)](https://ci.appveyor.com/project/yungez/vscode-ansible)

# Visual Studio Code extension for Ansible

## Overview
This extension helps to use [Ansible](https://www.ansible.com/) efficiently in VSCode.

## Features

  - Auto completion. Auto completion Ansible directives, modules and plugins from Ansible doc.
  - Code snippets.  Press `Ctrl + Space`, Ansible playbook code snippets will show up.
  - Syntax highlighting.
  - Run playbook from Terminal.
    - On Windows, run Ansible inside docker.
    - On Non-windows platform, provide option to run Ansible from docker or from local Ansible installation.
  - Run playbook from [Cloud Shell](https://azure.microsoft.com/en-us/features/cloud-shell/). 


## Requirements

|platform|prerequisite|
|--------|-----------|
|All| nodejs >= 6.0 |
|Windows/Other platforms choose docker|docker|
|Platforms choose local| Ansible |

## Usage
- Auto completion
- Code snippets  
    Press `Ctrl + Space` in playbook yml file, you'll see Ansible modules code snippets.    
    ![auto completion and code snippets](./images/authoring.gif)
    
- Run Ansible playbook commands  
  2 methods are supported to run Ansible playbook: *Run Ansible Playbook in Terminal* and *Run Ansible Playbook in Cloud Shell*.
  
  - Run Ansible Playbook in Terminal 
    1. Press `F1`, type: `ansible`, choose `Run Ansible Playbook in Terminal`.
    1. Input playbook file full path, or use default one.
    1. This step is optinal. If you want to run cloud provider specific Ansible modules, you need set cloud credentials in credential yaml file, default path is `$HOME/.vscode/ansible-credentials.yml`, or change credential file path by settings item  `ansible.credentialsFile`. Credential file template is at [here](https://github.com/VSChina/vscode-ansible/blob/master/config/credentials.yml).
    1. On Non-Windows platforms, option `docker` and `local` are supported. The `docker` option requires docker installed and the `local` option requires Ansible installed. To use `docker` option on other platforms, please configure docker run without sudo. 
    1. For Windows user, please share your Windows driver where vscode workspace sits on with docker. This is because the extension will map your workspace containing playbook with docker.   
       ![docker share driver](./images/dockerconfig.png)
       
       ***NOTE*** 
       Docker on windows is not stable as other platform, please try to restart docker and retry if met docker issue.

    

  - Run Ansible Playbook in [Cloud Shell](https://azure.microsoft.com/en-us/features/cloud-shell/) 
    1. **Important** Please setup Cloud Shell for first time usage in Azure Portal by following [this instruction](https://docs.microsoft.com/en-us/azure/cloud-shell/overview). After setup, input cmd `az account show` to learn your current subscription setting.
    1. Install [Azure Account](https://marketplace.visualstudio.com/items?itemName=ms-vscode.azure-account) VSCode extension, which is used for Azure login.
    1. Press `F1`, type: `Azure: Sign In`, do Azure login.
    1. Press `F1`, type: `ansible`, choose `Run Ansible Playbook in Cloud Shell`.
    1. Input playbook file full path, or use default one.
    1. Confirm awareness on Azure usage fee. Please refer to [this document](https://docs.microsoft.com/en-us/azure/cloud-shell/pricing) to learn more about Azure Cloud Shell pricing.
    


- Configuration  
  This extension provides 2 configurations in settings.json.
  - `ansible.credentialsFile`  
    This configuration is used to specify ansible credentials file path. Default is `$HOME/.vscode/ansible-credentials.yml`.
  - `ansible.termininalInitCommand`  
    This configuration is used to specify customized terminal init command. Default is docker run commands for docker, and 'ansible-playbook' for local setup.


## Feedback and Questions
You can submit bug or feature suggestion via [issues](https://github.com/VSChina/vscode-ansible/issues/new).

## License
[MIT license](./LICENSE.md).

## Telemetry
This extension collects telemetry data to help improve our products. Please read [Microsoft privacy statement](https://privacy.microsoft.com/en-us/privacystatement) to learn more. If you opt out to send telemetry data to Microsoft, please set below configuration in settings.json:
```
telemetry.enableTelemetry = false
```








