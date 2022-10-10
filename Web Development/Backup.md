# Daily backup of Database Collections

### Step 1: Download and Install putty
If Putty is not installed in your pc, then follow the following steps:
1. Visit [Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) website
2. From Package files section, download 64-bit x86 version of Putty
3. Install Putty

### Step 2: Collect Server IP and PPK file
TDRL Server's IP and PPK files can be found in `Prject Attachments` as shown below in the image.
![Project attachments](https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/Backup/Attachments.png)

### Step 3: Connect to Server through SSH
1. Open Putty application
2. Enter the server IP address in Host Name (or IP address) section, as shown in Figure 1
![Putty Home Screen](https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/Backup/Step-2.png)
*Figure 1: Enter IP address*
3. From the left navigation, Expand the SSH menu and then click on Auth menu, as shown in Figure 2
![PPK Select Screen](https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/Backup/Step-3.png)
*Figure 2: Select PPK file screen*
4. Click on the Browse button (Figure 3) and select the PPK file (Figure 4) you have downloaded and click on Open button (Figure 5)
![Browse button](https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/Backup/Step-4.png)
*Figure 3: Browse button to select PPK file*
![PPK Selection Dialog](https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/Backup/Step-5.png)
*Figure 4: PPK Selection Dialog*
![PPK Open Button](https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/Backup/Step-6.png)
*Figure 5: PPK Open Button*
5. Once PPK file is selected, from the left Navigation click on Session menu (Figure 6)
![Session Menu](https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/Backup/Step-7.png)
*Figure 6: PPK selected and Session menu*
6. Enter a name in Saved Sessions input box and click on the Save button to use the server in future. Now click on the Open button (Figure 7).
![Save Session for Future use](https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/Backup/Step-8.png)
*Figure 7: Save Session for Future use*
7. A terminal will pop-up. If everything is setup correctly, then the terminal will ask for a username. Enter `ec2-user` as the user. Generally in AWS servers, you need to use `ec2-user` to connect through SSH. 
![SSH Terminal and Login Credentials](https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/Backup/Step-9.png)
*Figure 8: SSH Terminal and Login Credentials*
8. Once you are logged in, then you need to setup TDRL backup package. To do that, continue reading...

### Step 4: Setup `backup` repository using SSH Terminal
1. Download the package in ELB
sudo yum install https://fastdl.mongodb.org/tools/db/mongodb-database-tools-amazon2-x86_64-100.5.0.rpm
Once downloaded, it will ask if you want to install or not, enter y to continue
2. Log into git
```
git config --global user.email "email@domain.com"
```
3. Download the repo
```
git clone https://<github_personal_access_token>@github.com/nazim2060/g-drive-backup.git
```
4. Go to the repo folder and install packages
```
cd g-drive-backup
npm install
```
5. Go to configuration folder and change the configs
```
cd configurations
vi config.json
```

Set `GOOGLE_FOLDER_ID` to `1pkytAHFw-5PexV6pM2t4mGVf95YXWT1m`

Set `DATABASE_NAME` to `RB-VENDOR`

Set `EMAIL_TEMPLATE_ID` to `d-69d20067e57f4a6d8a35116015ac616e`

Press `Esc` keyboard button. 

Enter `:wq` in the terminal and press `Enter`.

6. Set Permission
```
cd ../
cd utils
chmod u+x /home/ec2-user/g-drive-backup/utils/backup.sh
cd ../../
```

7. Setup cron ([More about cron-jon](https://www.freecodecamp.org/news/cron-jobs-in-linux/))
```
crontab –e
```
then enter the following command
```
01 18 * * * /home/ec2-user/g-drive-backup/utils/backup.sh
```
Press `Esc` keyboard button. 

Enter `:wq` in the terminal and press `Enter`.