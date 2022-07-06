# Github在Windows(10)下的免密

[toc]

小结：

- 如果想要免密可以一开始就不要设置passphrase口令
- 如果设置了需要免密在Windows下需要重新设置一系列配置
- 需要在**`cmd`**命令框里面操作，使用**git bash**无效



## 1. 前置条件

根据[这篇](https://stackoverflow.com/questions/18683092/how-to-run-ssh-add-on-windows)文章描述，在Windows(10)下设置免密，需要提前安装好：

- git公私钥配置：Make sure your **`id_rsa`** file is in the folder `c:\users\yourusername\.ssh`



## 2. 启动OpenSSH

2019年之后的Windows10，自带了OpenSSH。需要为此单独做一些配置，否则会和Git自带的SSH起[冲突](#1. Windows和Git的SSH冲突)。

> OpenSSH is available as part of Windows 10 which makes using SSH from cmd/powershell much easier in my opinion. It also doesn't rely on having git installed, unlike my previous solution.

1. Open **`Manage optional features`** from the start menu and make sure you have Open SSH Client in the list. If not, you should be able to add it.

2. Open **`Services`** from the start Menu

3. Scroll down to **`OpenSSH Authentication Agent`** > right click > properties

4. Change the Startup type from Disabled to any of the other 3 options. I have mine set to **`Automatic (Delayed Start)`**

5. Open cmd and type **`where ssh`** to confirm that the top listed path is in System32. Mine is installed at `C:\Windows\System32\OpenSSH\ssh.exe`. If it's not in the list you may need to close and reopen cmd.

   Once you've followed these steps, ssh-agent, ssh-add and all other ssh commands should now work from cmd. To start the agent you can simply type ssh-agent.

6. **Optional step/troubleshooting**: If you use git, you should set the **`GIT_SSH`** environment variable to the output of **`where ssh`** which you ran before (e.g `C:\Windows\System32\OpenSSH\ssh.exe`). 

   This is to stop inconsistencies between the version of ssh you're using (and your keys are added/generated with) and the version that git uses internally. This should prevent issues that are similar to this

**Some nice things about this solution:**

- You won't need to start the ssh-agent every time you restart your computer
- Identities that you've added (using ssh-add) will get automatically added after restarts. (It works for me, but you might possibly need a config file in your c:\Users\User\.ssh folder)
- You don't need git!
- You can register any rsa private key to the agent. The other solution will only pick up a key named `id_rsa`



## 3. ssh-add

[据说](https://superuser.com/questions/1010542/how-to-make-git-not-prompt-for-passphrase-for-ssh-key/1655228#1655228)在Windows下不能使用相对路径添加:

TDLR: For windows users,

- run `ssh-add "C:\\Users\\<your user>/.ssh/id_rsa"`
- not `ssh-add ~/.ssh/id_rsa`

```gas
C:\Windows\system32>ssh-add "c:\Users\lee.wang\.ssh\id_rsa"
Enter passphrase for c:\Users\lee.wang\.ssh\id_rsa:
Identity added: c:\Users\lee.wang\.ssh\id_rsa (youremail@domain.com)
```

<img src="./img/image-20220706143817281.png" alt="image-20220706143817281" style="zoom:80%;" /> 



## 4. 其他



### 1. Windows和Git的SSH冲突

<img src="./img/image-20220706144225657.png" alt="image-20220706144225657" style="zoom: 80%;" /> 

**Optional step/troubleshooting**: If you use git, you should set the **`GIT_SSH`** environment variable to the output of **`where ssh`** which you ran before (e.g `C:\Windows\System32\OpenSSH\ssh.exe`). 

This is to stop inconsistencies between the version of ssh you're using (and your keys are added/generated with) and the version that git uses internally. This should prevent issues that are similar to this

**To set `GIT_SSH` permanently**

<img src="./img/image-20220706144107457.png" alt="image-20220706144107457" style="zoom:80%;" />

1. Open File Explorer. Start-> type 'File Explorer' and click on it in the list.
2. Right-click 'This PC' and click on 'Properties'.
3. Click on 'Advanced system settings'.
4. Click the 'Environment Variables...' button.
5. Under 'User variables for your_user_name' click New...
6. Set `Variable name:` field to GIT_SSH
7. Set the `Variable value:` field to path-to-ssh.exe (typically `C:\Windows\System32\OpenSSH\ssh.exe`).
8. Click OK to dismiss the New User Variable dialog.
9. Click OK to dismiss the Environment Variables dialog.
10. Retry the steps in **Try Git + SSH** above.



-------------

如果在git bash 内遇到：

> git ssh authentication fails with ssh_askpass: posix_spawn: Unknown error

说明就是遇到了ssh冲突，这时候要切回cmd做git操作

### 2. cmd快捷切换到文件夹目录内

如果需要快捷切换到某个目录内，只要在当前目录栏直接输入**`cmd`**就可以直接打开一个命令栏，然后开始git相关操作

<img src="./img/image-20220706144330213.png" alt="image-20220706144330213" style="zoom: 67%;" /> <img src="./img/image-20220706144358688.png" alt="image-20220706144358688" style="zoom:67%;" />





## Reference

1. [How to run ssh-add on windows?](https://stackoverflow.com/questions/18683092/how-to-run-ssh-add-on-windows)
1. [Why git can't remember my passphrase under Windows](https://stackoverflow.com/questions/370030/why-git-cant-remember-my-passphrase-under-windows)
1. [How to make git not prompt for passphrase for ssh key?](https://superuser.com/questions/1010542/how-to-make-git-not-prompt-for-passphrase-for-ssh-key/1655228#1655228)
1. [SSH Key - Still asking for password and passphrase](https://stackoverflow.com/questions/21095054/ssh-key-still-asking-for-password-and-passphrase?page=1&tab=scoredesc#tab-top)