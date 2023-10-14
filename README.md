![Rclone Docker Gui](https://i.ibb.co/bvBZFxr/Screenshot-2023-10-14-at-17-53-27.png)

# Installation

Local environment requirements (Config to Rclone File) :

- [Rclone](https://rclone.org/install/)

To run on platforms such as server environment requirements(if there is rclone.config file) :

- [Docker](https://www.docker.com/)

## **Install with Laravel Sail (with Docker)**

🛑Step 1 : **Clone Repo**

```bash
  git clone https://github.com/mahallemuhtari/Rclone-Docker-Web-Gui.git
  cd Rclone-Docker-Web-Gui
```
or Or you can download it as a zip file from github.com

🧐Step 2: **Change Username and Password**

Edit docker-compose.yaml.

Default Username=admin

Default Passwor=123
```bash
command: rcd --rc-web-gui --rc-addr 0.0.0.0:5572 --rc-user CHANGE_ME_USERNAME --rc-pass CHANGE_ME_PASSWORD
```

🛑Step 3: **Docker Compose Up**

```bash
docker compose up
```
Result:

```bash

rclone_rclone  | 2023/10/14 14:59:57 ERROR : Error reading tag file at /root/.cache/rclone/webgui/tag
rclone_rclone  | 2023/10/14 14:59:57 NOTICE: A new release for gui (v2.0.5) is present at https://github.com/rclone/rclone-webui-react/releases/download/v2.0.5/currentbuild.zip
rclone_rclone  | 2023/10/14 14:59:57 NOTICE: Downloading webgui binary. Please wait. [Size: 4763452, Path :  /root/.cache/rclone/webgui/v2.0.5.zip]
rclone_rclone  | 2023/10/14 14:59:59 NOTICE: Unzipping webgui binary
rclone_rclone  | 2023/10/14 14:59:59 NOTICE: Serving Web GUI
rclone_rclone  | 2023/10/14 14:59:59 NOTICE: Serving remote control on http://[::]:5572/
rclone_rclone  | 2023/10/14 14:59:59 ERROR : Failed to open Web GUI in browser: exec: "xdg-open": executable file not found in $PATH. Manually access it at: http://admin:123@[::]:5572/?login_token=YWRtaW46MTIz
```

🎉🎉 Finish Step 4: **Open Browser This Link**

Auto Login = `
http://admin:123@[::]:5572/?login_token=YWRtaW46MTIz
`
or 

Use Username and Password = `
http://127.0.0.1:5572/?login_token=YWRtaW46MTIz
`

# Rclone Remote Added Basically

⭐️ **[LOCAL MACHINE]**: Install Rclone Local Machine on Linux/macOS/BSD systems, run:


```bash
  sudo -v ; curl https://rclone.org/install.sh | sudo bash
```


[Rclone Install Link All System Windows,Linux,OsX... ](https://rclone.org/install/)


## On Docker


🛑Step 1: **Learn to Docker Container ID**


```bash
docker ps
```
Result:

```bash

❯ docker ps     

CONTAINER ID   IMAGE     COMMAND     CREATED   STATUS      PORTS    NAMES
2a9514454ac9   rclone/rclone      "rclone rcd --rc-web…"   8 minutes ago   Up 8 minutes       0.0.0.0:5572->5572/tcp, 0.0.0.0:53682->53682/tcp   rclone_rclone
```

Selecet Thish ID example **2a9514454ac9**



🛑Step 2: **Login Docker Terminal**


```bash
docker exec -it 2a9514454ac9 sh
```


🛑Step 3: **Run Rclone Config**

[Rclone Config Docs](https://rclone.org/docs/)

```bash
rclone config
```

Result:

```bash
n) New remote
s) Set configuration password
q) Quit config
n/s/q> n

.
.
.
.
Enter name for new remote.
name> MyDrive
.
.
.
//Select List to Connect Storage for example Google Drive
Storage> drive
.
.
.
client_id>
.
.
client_secret>
.
.
.
Press Enter to leave empty.
 1 / Full access all files, excluding Application Data Folder.
   \ (drive)
 2 / Read-only access to file metadata and file contents.
   \ (drive.readonly)
   / Access to files created by rclone only.
 3 | These are visible in the drive website.
   | File authorization is revoked when the user deauthorizes the app.
   \ (drive.file)
   / Allows read and write access to the Application Data folder.
 4 | This is not visible in the drive website.
   \ (drive.appfolder)
   / Allows read-only access to file metadata but
 5 | does not allow any access to read or download file content.
   \ (drive.metadata.readonly)
scope>1
.
.
.
.
service_account_file>
.
.
.
Edit advanced config?
y) Yes
n) No (default)
y/n> n
Use web browser to automatically authenticate rclone with remote?
 * Say Y if the machine running rclone has a web browser you can use
 * Say N if running rclone on a (remote) machine without web browser access
If not sure try Y. If Y failed, try N.

y) Yes (default)
n) No
y/n>n


Option config_token.
For this to work, you will need rclone available on a machine that has
a web browser available.
For more help and alternate methods see: https://rclone.org/remote_setup/
Execute the following on the machine with the web browser (same rclone
version recommended):
	rclone authorize "drive" "eyJzY29UuhnUIUaXZlIn0"
Then paste the result.
Enter a value.
```
1- Copy to command this result = `rclone authorize "drive" "eyJzY29UuhnUIUaXZlIn0"`

2- **Wait This Step and Open New Terminal Dont Close This Terminal**

3- After this stage, we will continue from the local machine.



## On Local Machine


🛑Step 4: **Run This Command**


```bash
rclone authorize "drive" "eyJzY29UuhnUIUaXZlIn0"
```



🛑Step 5: **Log in and Authorize Google drive on Browser**


```bash
rclone authorize "drive" "eyJzY29UuhnUIUaXZlIn0"
```

Result:

```bash

2023/10/14 18:19:39 NOTICE: If your browser doesn't open automatically go to the following link: http://127.0.0.1:53682/auth?state=b9AEbzdssdsadcfasdf
2023/10/14 18:19:39 NOTICE: Log in and authorize rclone for access
2023/10/14 18:19:39 NOTICE: Waiting for code...

```

After to Login: 
```bash

2023/10/14 18:19:39 NOTICE: If your browser doesn't open automatically go to the following link: http://127.0.0.1:53682/auth?state=b9AEbzdssdsadcfasdf
2023/10/14 18:19:39 NOTICE: Log in and authorize rclone for access
2023/10/14 18:19:39 NOTICE: Waiting for code...
2023/10/14 18:21:26 NOTICE: Got code
Paste the following into your remote machine --->
oZlFyTGJ1U4Z3IxQXBEUFJKTHRiOWtGeWNKbjliMkxyYlp3YUNnWUtBZU1TQVJFU0ZRR09jTm5DMzRsc0xxcGlXR1p6bW9xX3FyNTU3dzAxNzFcIixcInRva2VuX3R5cGVcIjpcIkJlYXJlclwiLFwicmVmcmVzaF90b2tlblwiOlwiMS8vMDNET2ZySVVzclFhNENnWUlBUkFBR0FNU053Ri1MOUlydFAyOD4Z3IxQXBEUFJKTHRiOWtGeWNKbjliMkxyYlp3YUNnWUtBZU1TQVJFU0ZRR09jTm5DMzRsc0xxcGlXR1p6bW9xX3FyNTU3dzAxNzFcIixcInRva2VuX3R5cGVcIjpcIkJlYXJlclwiLFwicmVmcmVzaF90b2tlblwiOlwiMS8vMDNET2ZySVVzclFhNENnWUlBUkFBR0FNU053Ri1MOUlydFAyODVMWXhXSVZ3dkFFdGEwdFZtZ2VMbEJ4S181clMxc0ZBOTc5bG1sd2hWZxQXBEUFJKTHRiOWtGeWNKbjliMkxyYlp3YUNnWUtBZU1TQVJFU0ZRR09jTm5DMzRsc0xxcGlXR1p6bW9xX3FyNTU3dzAxNzFcIixcIn
<---End paste

```

Copy to result code:

`
oZlFyTGJ1U4Z3IxQXBEUFJKTHRiOWtGeWNKbjliMkxyYlp3YUNnWUtBZU1TQVJFU0ZRR09jTm5DMzRsc0xxcGlXR1p6bW9xX3FyNTU3dzAxNzFcIixcInRva2VuX3R5cGVcIjpcIkJlYXJlclwiLFwicmVmcmVzaF90b2tlblwiOlwiMS8vMDNET2ZySVVzclFhNENnWUlBUkFBR0FNU053Ri1MOUlydFAyOD4Z3IxQXBEUFJKTHRiOWtGeWNKbjliMkxyYlp3YUNnWUtBZU1TQVJFU0ZRR09jTm5DMzRsc0xxcGlXR1p6bW9xX3FyNTU3dzAxNzFcIixcInRva2VuX3R5cGVcIjpcIkJlYXJlclwiLFwicmVmcmVzaF90b2tlblwiOlwiMS8vMDNET2ZySVVzclFhNENnWUlBUkFBR0FNU053Ri1MOUlydFAyODVMWXhXSVZ3dkFFdGEwdFZtZ2VMbEJ4S181clMxc0ZBOTc5bG1sd2hWZxQXBEUFJKTHRiOWtGeWNKbjliMkxyYlp3YUNnWUtBZU1TQVJFU0ZRR09jTm5DMzRsc0xxcGlXR1p6bW9xX3FyNTU3dzAxNzFcIixcIn
`



## On Docker


🛑Step 6: **Paste Code  Docker Terminal And Press Enter**




Result:

```bash

config_token>oZlFyTGJ1U4Z3IxQXBEUFJKTHRiOWtGeWNKbjliMkxyYlp3YUNnWUtBZU1TQVJFU0ZRR09jTm5DMzRsc0xxcGlXR1p6bW9xX3FyNTU3dzAxNzFcIixcInRva2VuX3R5cGVcIjpcIkJlYXJlclwiLFwicmVmcmVzaF90b2tlblwiOlwiMS8vMDNET2ZySVVzclFhNENnWUlBUkFBR0FNU053Ri1MOUlydFAyOD4Z3IxQXBEUFJKTHRiOWtGeWNKbjliMkxyYlp3YUNnWUtBZU1TQVJFU0ZRR09jTm5DMzRsc0xxcGlXR1p6bW9xX3FyNTU3dzAxNzFcIixcInRva2VuX3R5cGVcIjpcIkJlYXJlclwiLFwicmVmcmVzaF90b2tlblwiOlwiMS8vMDNET2ZySVVzclFhNENnWUlBUkFBR0FNU053Ri1MOUlydFAyODVMWXhXSVZ3dkFFdGEwdFZtZ2VMbEJ4S181clMxc0ZBOTc5bG1sd2hWZxQXBEUFJKTHRiOWtGeWNKbjliMkxyYlp3YUNnWUtBZU1TQVJFU0ZRR09jTm5DMzRsc0xxcGlXR1p6bW9xX3FyNTU3dzAxNzFcIixcIn

Configure this as a Shared Drive (Team Drive)?

y) Yes
n) No (default)
y/n> n

Keep this "MyDrive" remote?
y) Yes this is OK (default)
e) Edit this remote
d) Delete this remote
y/e/d>y
```

🎉🎉🎉🎉 All the adjustments are completed, from now on it is up to your imagination, you can use it as you wish. 🎉🎉🎉🎉

## Thank you for your help

[Rclone](https://rclone.org/sponsor/)
[darthShadow - Anagh Kumar Baranwal | on forum Rclone](https://forum.rclone.org/t/docker-rclone-cannot-open-auth-page-when-config/19110/2)
[DavidA - David Amor | on forum Rclone](https://forum.rclone.org/t/how-to-set-up-rclone-webgui-server-as-a-docker-container/14330)








