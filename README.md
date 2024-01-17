# VariousREADME

# Engage-Core-App Set Up Guide:

## Install VSC and Node:
  Node: https://nodejs.org/en/download/ 
  <br/>
  VSC: https://code.visualstudio.com/download
### Install NVM (recommended):
  Link to install: https://github.com/nvm-sh/nvm#install--update-script
  <br/>
  Note: Incase npm-related issues arise, utilize nvm to downgrade to node v18.8.0
  <br/>
  <br/>
  Commands:
  ```
    nvm install 18.8.0
    nvm use 18.8.0
    node --version
  ```
## Clone repo
  Repo link: https://github.com/NavicoGroup/engage-core-app
  <br/>
  You can clone using HTTPS or SSH (recommended):
    Good guide for cloning using SSH: https://phoenixnap.com/kb/git-clone-ssh
## Azure DevOps Personal Token:
  Navigate to Azure Devops: https://dev.azure.com/bconline
  <br/>
  <br/>
  Create a Personal Access token:
  <br/>
  <br/>
    Good guide for creating a PAT: https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate
    <br/>
    Your PAT should have a Full access Scope. Don't forget to save your generated PAT in some secure file.
  <br/>
  <br/>
  Run this command and enter your PAT when prompted to:
  ```
  node -e "require('readline') .createInterface({input:process.stdin,output:process.stdout,historySize:0}) .question('PAT> ',p => { b64=Buffer.from(p.trim()).toString('base64');console.log(b64);process.exit(); })"
  ```
  Save the output in some secure file. The output is the encoded version of your PAT. Both the encoded and decoded (original) versions will be used 
  <br/>
  <br/>
## Set up the Enviroment Variables
  You will need to set up two enviroment variables: Good guide on env vars (https://phoenixnap.com/kb/set-environment-variable-mac)
  <br/>
  NPM_USER=(The username part of your email addres (i.e. Adam.Khoukhi@navicogroup.com -> Adam.Khoukhi)
  <br/>
  NPM_PASS=(The encoded PAT generated previously)
  
  
    
