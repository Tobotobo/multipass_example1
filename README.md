# multipass_example1


https://multipass.run/docs/installing-on-windows

multipass-1.13.1+win-win64.exe  
約 30 MB  
ダブルクリックすると GUI のインストーラーが起動する。  

インストール先
```
C:\Program Files\Multipass\bin
```
↑ Multipass フォルダの容量は約 100 MB  
PATH が長すぎると警告が表示されて追加されない。  
手動で追加した。

VirtualBox  
インストール中に Hyper-V か VirtualBox かの選択あり。サイトの案内の以下は未実施
```
multipass set local.driver=virtualbox
```



```
> multipass version
multipass   1.13.1+win
multipassd  1.13.1+win
```

```
> multipass launch
Launched: creative-tardigrade
```

```
> multipass list
Name                    State             IPv4             Image
creative-tardigrade     Running           N/A              Ubuntu 22.04 LTS
```

```
> multipass shell
Launched: primary
Skipping mount due to disabled mounts feature
Welcome to Ubuntu 22.04.4 LTS (GNU/Linux 5.15.0-97-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

  System information as of Fri Mar  8 02:25:46 JST 2024

  System load:  0.544921875       Processes:               97       
  Usage of /:   33.0% of 4.67GB   Users logged in:         0        
  Memory usage: 24%               IPv4 address for enp0s3: 10.0.2.15
  Swap usage:   0%


Expanded Security Maintenance for Applications is not enabled.      

1 update can be applied immediately.
1 of these updates is a standard security update.
To see these additional updates run: apt list --upgradable

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@primary:~$ 
```

上記が表示された状態で、VirtualBox マネージャーに表示されず。  
念のため Hyper-V マネージャも見たがこちらも表示されず。リストには上がってこない？

↓ primary が増えてた。shell で対象を指定しないと勝手に生えてくる？
```
> multipass list
Name                    State             IPv4             Image
primary                 Running           N/A              Ubuntu 22.04 LTS
creative-tardigrade     Running           N/A              Ubuntu 22.04 LTS
```

```
> multipass delete --all
> multipass list
Name                    State             IPv4             Image
primary                 Deleted           --               Ubuntu 22.04 LTS
creative-tardigrade     Deleted           --               Ubuntu 22.04 LTS
```

```
> multipass purge
> multipass list
No instances found.
```