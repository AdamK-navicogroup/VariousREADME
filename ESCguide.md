
# Empower-Service-Core Set Up Guide:

## 1. Install VSC and Node:
  - Node: https://nodejs.org/en/download/ 
  - VSC: https://code.visualstudio.com/download

## 2. Install Docker Desktop:
  - Docker Desktop:
    - Mac: https://docs.docker.com/desktop/install/mac-install/
    - Windows: https://docs.docker.com/desktop/install/windows-install/
  - Finish Setting up Docker Desktop
    - Select `Use recommended settings (requires password)` and click `Finish`
    - Click on `Continue without signing in` and `skip`

## 3. Clone Github Repositories:
  - Inside your documents folder, clone the following repositories:
    - empower-service-core: https://github.com/NavicoGroup/empower-service-core
    - empower-service-policy: https://github.com/NavicoGroup/empower-service-policy
  - You can clone using HTTPS or SSH (recommended):
    Good guide for cloning using SSH: https://phoenixnap.com/kb/git-clone-ssh

## 4. Set up the backend:
  - Download `navico-backend-setup.zip` found in this directory and move it to your `documents` folder.
  - Extract and open the folder on VSC.
  - Inside you will find a text file named `convert2dotenv.txt`. In the same directory as the text file, create a `.env` file and copy the content's of `convert2dotenv.txt` to that env file. 

## 5. Set up Empower-service-policy:
  - Download `Dockerfile.local` found in this directory.
  - Inside the `empower-service-policy` you cloned earlier, add the `Dockerfile.local` file in the outermost directory (same directory as the `Dockerfile` and `package.json`)

## 6. Create and start containers:
  - Open back your `navico-backend-setup` on VSC
  - Open a new terminal and run the command:
    ```
    docker-compose up -d --build
    ```


## 4. Set up the Enviroment Variables
  You will need to set up two enviroment variables: Good guide on env vars (https://phoenixnap.com/kb/set-environment-variable-mac)
  <br/>
  <br/>
NPM_USER=(The username part of your email addres (i.e. Adam.Khoukhi@navicogroup.com -> Adam.Khoukhi)
<br/><br/>
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
## 6. BLE setup
  - Install the Azure CLI by executing the following command:
<code>brew update && brew install azure-cli</code>.

  - Login with Azure CLI by executig the following commands:
    - <code>az login</code> and complete the authentication process
    - <code>az devOps login --organization https://dev.azure.com/bconline</code>
and provide your personal access token when requested. The personal access token is the NPM token(Without encoding base64).

  - Install azure universal package using `gem install 'cocoapods-azure-universal-packages'`
  - Execute the command <code>pod install</code>.
  Once yarn is complete, navigate to the `ios` folder and execute the command `pod install`
  ### Troubleshooting
  #### Error:
  ```
    zsh: command not found: pod
  ```
  #### Fix:
  Install pod
     ```
          sudo gem install cocoapods
      ```
 
  #### Error:
  ```
    Error loading plugin file  '/Library/Ruby/Gems/2.6.0/gems/cocoapods-azure-universal-packages-0.1.0/lib/cocoapods_plugin.rb'.

    Gem::ConflictError - Unable to activate cocoapods-azure-universal-packages-0.1.0, because cocoapods-downloader-2.0 conflicts with cocoapods-downloader (~> 1.0)

    Your Podfile requires that the plugin 'cocoapods-azure-universal-packages' be installed. Please install it and try installation again.
  ```
  #### Fix:
  Run the commands:
  
     
        sudo gem uninstall jazzy --all --executables
        
        sudo gem uninstall cocoapods --all --executables
        
        sudo gem uninstall cocoapods-core --all --executables
        
        sudo gem uninstall cocoapods-downloader --all --executables
      
     
  Then the commands:
  
     
        sudo gem install cocoapods-core -v 1.12.1
        
        sudo gem install cocoapods -v 1.12.1
        
        sudo gem install cocoapods-downloader -v 1.6.3
        
        sudo gem install jazzy
        
        sudo gem install cocoapods-azure-universal-packages 
        
    
  
  #### Error:
  ```
    Cloning spec repo `navicogroup-engage-ios-podspecs-1` from `https://github.com/NavicoGroup/engage-ios-podspecs`
    [!] Unable to add a source with url `https://github.com/NavicoGroup/engage-ios-podspecs` named `navicogroup-engage-ios-podspecs-1`.
    You can try adding it manually in `/Users/akhoukhi/.cocoapods/repos` or via `pod repo add`.
  ```
  #### Fix:
  Try adding manually:
  
     
       pod repo add navicogroup-engage-ios-podspecs git@github.com:NavicoGroup/engage-ios-podspecs.git
     
     
  If that doesn't work, navigate to the  `Podfile`:
  - Replace
    ```  
      source 'https://github.com/NavicoGroup/engage-ios-podspecs'
    ```
  - With
    ```
      source 'git@github.com:NavicoGroup/engage-ios-podspecs.git'
    ```

  #### Error:
  ```
    [!] Error installing EngageBleCore
    [!] /opt/homebrew/bin/az artifacts universal download --organization https://dev.azure.com/bconline --feed MobileAppDevelopment --name engage-ios-ble-core --version 0.0.27 --path /var/folders/g7/k20kctg9615c9ynpz30p9k500000gn/T/d20240117-22914-2znfjr --project ASG --scope project
    ...
  
    OSError: [Errno 86] Bad CPU type in executable: '/Users/akhoukhi/.azure/azuredevops/cli/tools/artifacttool/ArtifactTool_osx-x64_0.2.300/artifacttool'
    To check existing issues, please visit: https://github.com/Azure/azure-cli/issues
  ```
  #### Fix:
  Install and use Rosetta
    <br/>
    
  1. In Finder, navigate to the  `Terminal` Application
  
  2. Right-Click the application and click on `Get Info`

  3. Inside the General category, check the `Open using Rosetta` option
  
  4. Open a new Terminal
  
  5. Run the commands:
    
     ```  
       sudo gem uninstall cocoapods --all --executables

       sudo gem install cocoapods -v 1.12.1

       softwareupdate --install-rosetta

       pod install
     
     ```
  #### Error:
  ```
    Installing glog (0.3.5)
    [!] /bin/bash -c 
    set -e
    #!/bin/bash
    ...

    checking whether the C compiler works... no
    xcrun: error: SDK "iphoneos" cannot be located
    xcrun: error: SDK "iphoneos" cannot be located
    xcrun: error: SDK "iphoneos" cannot be located
    xcrun: error: unable to lookup item 'Path' in SDK 'iphoneos'
    ...

    configure: error: C compiler cannot create executables
    See `config.log' for more details
    
  ```
  #### Fix:
  1. Launch XCode
  2. On the top bar, click on `XCode` then `Settings`
  3. Navigate to `Locations`
  4. Make sure there's a dropdown option selected for the command line tools
  5. NOTE: Even if you're seeing Command Line Tools dropdown being selected with proper version, you might want to re-select it again.
  6. To know if successful, the light text underneath the Command Line Tools dropdown should say `/Applications/Xcode.app`


## Congratulations! You are all set up!

## To run the App:

1. Run the command:
   ```
   npx react-native run-ios
   ```
### Troubleshooting

  #### Error:
  If you are a Mac user (Apple Silicon), and the build fails with a Linker error:

  #### Fix:
  1. Open XCode
  2. Inside the Pods `xcodeproj`, add `arm64` to the `Excluded Architectures`
     ![plot](./ECAImages/PodArm64.png)
  3. Once done, re-run the commands below
    ```
    yarn

    cd ios
    
    pod install
    
    cd ..
    
    npx react-native run-ios

  #### Error:
  If your login fails with an API error or something as shown below:
  ```
  [CodePush] Network request failed


  2024-01-18T14:41:20.814Z | REALM | ERROR | Could not login api-key based Realm user AppError: Network request failed {"name":"AppError","logs":"","code":"CustomError"}

  ```
  #### Fix:
  Try turning off `GlobalProtect` and `ZScaler` to fix it.
