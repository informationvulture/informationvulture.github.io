---
tags: Linux
---

## Basic VM Setup (Ubuntu + Debian)

I like using DigitalOcean to setup VM's for personal projects. The one thing that I constantly find myself doing is creating a new user to follow the security principle of not using the root account for daily tasks. Actually, I found that most security guides recommend disabling the root account completely.

Here's the steps that I always forget, no matter how many times I do them. I know this works on **Ubuntu** and **Debian**, but I haven't tried other distros yet.

Getting the actual new user:
```bash
adduser newuser # create the new user
usermod -aG sudo newuser # add them to the sudoers file
```

Get SSH to work (hint: replace $USER with the username of the new user you created above if you aren't logged in as them):
```bash
mkdir /home/$USER/.ssh
chmod 700 /home/$USER/.ssh
sudo cp /root/.ssh/authorized_keys /home/$USER/.ssh/authorized_keys
sudo chown -R $USER:$USER /home/$USER/.ssh
sudo chmod 600 /home/$USER/.ssh/authorized_keys
```


##### Sources
https://askubuntu.com/questions/1218023/copying-ssh-key-from-root-to-another-user-on-same-machine
https://www.digitalocean.com/community/tutorials/how-to-add-and-delete-users-on-ubuntu-20-04
