# Development Server: Getting Started

## Setting up a Local Development Server

Ideally we start with a blank (Ubuntu Server)[https://ubuntu.com/download/server] VM.
Note: If you are using an M1 Mac you will need to use the ARM version of the Ubuntu Server.

1. Start by cloning the 'REMAR-web-ui-and-API' repo to the home folder on the VM using:
    ```
        git clone https://github.com/REMAR-Project/REMAR-web-ui-and-API
    ```

---
### Updating code to work on:

1. Next we need to change some path names so the dev server will work like the deployed server.

    First edit the crabblerweb python file using:

    ```
    nano ~/REMAR-web-ui-and-API/API/src/crabblerweb/crabblerweb.py
    ```

    We want to change line 23 from: 
    ```
    log_pathname = '/etc/crab/logs/crabbler_web.log' 
    ```
    To 
    ```
    log_pathname = 'var/crabbler_web.log'
    ```

2. In the same file we also want to update the pathname in the legacy_api_auth() function from:
    ```
    pathname = '/etc/crab/API/data/auth/'+filename
    ```
    to
    ```
    pathname = '../API/data/auth/'+filename
    ```

3. We must also update the pathname in the legacy_api_users() function from:
     ```
    pathname = '/etc/crab/API/data/users/'+filename
    ```
    to
    ```
    pathname = '../API/data/users/'+filename
    ```

4. We must update the pathnames in the up() function from:
    ```
    path = '/etc/crab/API/data/sightings/' + year + "/" + month + "/" + day + "/"
    ```
    to
    ```
    path = '../API/data/sightings/' + year + "/" + month + "/" + day + "/"
    ```
5. We must also update the following two lines in the up() function:
   ```
    os.system("source /etc/crab/crabenv/bin/activate")
    os.system("/etc/crab/admin-website/PythonScripts/main.py")
    ```
    to:
    ```
    os.system("source ../API/env/bin/activate")
    os.system("../admin-website/PythonScripts/main.py")
    ```
---
## Installing/Setting Up The Python Environment 

Run the following script:

```
sudo apt update
sudo apt install python2 pip virtualenv -y

cd ~/REMAR-web-ui-and-API/API

virtualenv -p /usr/bin/python2 env

source env/bin/activate
pip install -r requirements.txt

mkdir var
sudo touch var/crabblerweb.log

mkdir data && mkdir data/auth && mkdir data/sightings && mkdir data/users

clear

echo Making start script

echo "cd ~/REMAR-web-ui-and-API/API && source env/bin/activate && python src/crabblerweb/crabblerweb.py" > ~/start.sh

echo ===========================================
echo SET UP FINISHED - RUNNING TESTS
echo ===========================================

python test/crabblerwebtest/crabblerwebtest.py

deactivate
chmod +x ~/start.sh

```