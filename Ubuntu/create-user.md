# Create New User in Ubuntu

### 1. Open a Terminal
### 2. Add a New User with a Specified Home Directory
``` bash
sudo useradd -m -d /home/sam sam
```



### 3. Set a Password for the New User
``` bash 
sudo passwd sam
```


### 4. Add User to Sudo Group
``` bash 
sudo usermod -aG sudo sam

```


### 5. Verify the User's Groups
``` bash 
groups sam
```


### 6. Check the Home Directory
``` bash 
ls -ld /home/sam
```


### 7. Set the shell if it's missing:
``` bash 
sudo usermod -s /bin/bash sam
```


### 8. Switch to the user
``` bash 
su - sam
```


### 9. Set Up SSH Access (Optional)
create the .ssh directory:

``` bash 
mkdir -p ~/.ssh
chmod 700 ~/.ssh
```


Add your public key to the authorized_keys file:
``` bash 
nano ~/.ssh/authorized_keys
```


Paste your public key into this file, save, and exit the editor. Then set the appropriate permissions:
``` bash 
chmod 600 ~/.ssh/authorized_keys
```



``` bash 

```