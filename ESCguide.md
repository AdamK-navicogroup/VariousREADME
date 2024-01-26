
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
  - If success, open back the `Docker Desktop` app. Your screen should resemble this:
    <br/>
    <br/>
    ![docker screen 1](./ESCImages/docker1.png)
    <br/>
    <br/>
    ![docker screen 2](./ESCImages/docker2.png)
    <br/>
    <br/>

## 7. Set up MongoDB:
  - Install MongoDB Compass: https://www.mongodb.com/try/download/compass
  - Complete set up and open the app, you will see a screen with `New Connection` in the middle.
    <br/>
    <br/>
    ![docker screen 1](./ESCImages/docker1.png)
    <br/>
    <br/>
  - Connect to a MongoDB deployment 
