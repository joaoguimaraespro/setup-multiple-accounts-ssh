# Tutorial for setup multiple git accounts via ssh


First step, you need to put the public ssh keys in the directory ~/ssh and rename them according to the accounts e.g. work-gitlab.pub 

After completing the first step, you must modify or create the config file in the ~/ssh directory and copy the following content, replacing the variables according to your configuration preferences

- You can only change the following variables: 

   - Host, for whatever you prefer;
   - HostName, to the host of your version control platform, e.g. gitlab.com, github.com;
   - IdentityFile, for path where the ssh key corresponding to the host is allocated.
   
<br/>

```
Host personal-gitlab
     HostName gitlab.com
     User git
     IdentityFile ~/.ssh/personal-gitlab.pub
     IdentitiesOnly yes

Host work-gitlab
     HostName gitlab.com
     User git
     IdentityFile ~/.ssh/work-gitlab.pub
     IdentitiesOnly yes

Host personal-github
     HostName github.com
     User git
     IdentityFile ~/.ssh/personal-github.pub
     IdentitiesOnly yes

Host work-github
     HostName github.com
     User git
     IdentityFile ~/.ssh/work-github.pub
     IdentitiesOnly yes

```

Finally, you need to run the following command in the cmd terminal

```
git config --global core.sshCommand "C:\\\\Windows\\\\System32\\\\OpenSSH\\\\ssh.exe"

```
or 

"C:\\Windows\\SysNative\\OpenSSH\\ssh.exe"

<br/>

# Testing

To test the connection via ssh with your accounts run the following commands:

```bash
ssh ${Host}
```

To clone a repository run the following command:

```bash
git clone ${Host}:${Username}/${NameOfRepository}.git
```

In my case I run the following commands:

```bash
ssh work-github
```

```bash
git clone work-github:${Username}/${NameOfRepository}.git
```
Run the following commands in your repository directory

```bash
git remote set-url origin workgithub:${Username}/${NameOfRepository}.git
```

<br/>



# Author

 **João Guimarães, [Github](https://github.com/joaoguimaraespro)**
