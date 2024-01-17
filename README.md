# VariousREADME

# Engage-Core-App Set Up Guide:

## 1. Install VSC and Node:
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
## 2. Clone repo
  Repo link: https://github.com/NavicoGroup/engage-core-app
  <br/>
  You can clone using HTTPS or SSH (recommended):
    Good guide for cloning using SSH: https://phoenixnap.com/kb/git-clone-ssh
## 3. Azure DevOps Personal Token:
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
## 4. Set up the Enviroment Variables
  You will need to set up two enviroment variables: Good guide on env vars (https://phoenixnap.com/kb/set-environment-variable-mac)
  <br/>
  NPM_USER=(The username part of your email addres (i.e. Adam.Khoukhi@navicogroup.com -> Adam.Khoukhi)
  <br/>
  NPM_PASS=(The encoded PAT generated previously)
  <br/><br/>
  To know if you have successfully added the env vars:
  <br/>
  <br/>
  Run the command:
  
  ```
  env | grep NPM   
  ```

  The output should look something like:
  
  ```
  NPM_USER=Adam.Khoukhi
  NPM_PASS=dTZxZHpkYXVpZTVpZXN1MnJtY3FjbnZ6aXd4enV4aXZmcm92cHY0aGR5NXFzaXZjaGducQ==
  ```
### Troubleshooting
  If you are having trouble adding the env vars then follow the steps below:
  <br/>
  1. Run the command:
     ```
     sudo nano ~/.bash_profile
     ```
  2. Inside Add the following lines and save:
     ```
     export NPM_USER=<Your username>
     export NPM_PASS=<Your encoded PAT>
     ```
  3. Run the command:
     ```
      source ~/.bash_profile
     ```
  ## Note:
  In future steps, make sure that the env variables are present by running the following command in your terminal:
  <br/>
     ```
      source ~/.bash_profile
     ```
## 5. Running Yarn
  Open a terminal in VSC and inside the `engage-core-app` run the command `yarn`.
  ### Troubleshooting
  #### Error:
  ```
    Error: Failed to replace env in config: {NPM_USER}
  ```
  #### Fix:
  Run the command:
     ```
       source ~/.bash_profile
     ```
  #### Error:
  ```
    Error: /Users/akhoukhi/Documents/engage-core-app/node_modules/realm: Command failed.
    Exit code: 127
    ...
    Output:
    prebuild-install warn install unable to get local issuer certificate
  ```
  #### Fix:
  Try downgrading your node version to 18.8 then re-executing `yarn`:
  ```
    nvm install 18.8.0
    nvm use 18.8.0
    node --version
  ```
  If that doesn't resolve it, try executing the command below then re-executing `yarn`:
  ```
    npm set strict-ssl=false
  ```
  If that also doesn't work, try executing `yarn` using the command below:
  ```
  NODE_TLS_REJECT_UNAUTHORIZED=0 yarn
  ```
### 6. Pod install
  Once yarn is complete, navigate to the `ios` folder and execute the command `pod install`
  
  
  
      
    
    
  
  
    
