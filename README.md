## Qemu Web Desktop - Soleil Software Setup

For the ultimate steps in virtualization... For some reason you might want to run VMs in browser (say again it was to share access.)

That first brought me to the noVNC project. 

But then found this project called "soleil software" whci uses noVNC but makes it more straight-forward for our use case.

[soleil software](https://gitlab.com/soleil-data-treatment/soleil-software-projects/qemu-web-desktop/-/blob/master/CONFIGURE.md)

`sudo apt install qemu-web-desktop` 

----

Where the machines live: 
`/var/lib/qemu-web-desktop/machines`

To insert a new one simply put it's file into the downloads folder:
(You can use `sudo mv source destination`)

`/var/lib/qemu-web-desktop/machines/downloads/deb.iso/<YOURISOORCQCOW2HERE>`

And inside it, your iso. Yes this is confusing :D 

Then run `sudo qwdctl download`
But then it will create a link as such:

![image](https://github.com/user-attachments/assets/83a621d4-ba55-4053-8b10-fffe5d2432cf)

You just have to figure out the structure: into downloads goes other directories (a machine) and inside it it's ISO or Disk. 

In our machine config we can add:
Find the other config files: `/etc/qemu-web-desktop`
`sudo nano machines.conf`

Read the top instructions they are explained nicely. We can simply add:
```
[deb.iso]
description=Debian
```

Then run `sudo qwdctl download` to refresh again.

We can now naviguate to to main interface:
```http://localhost/qemu-web-desktop/``` 

Enter an ID and click create:

![utli](https://github.com/user-attachments/assets/9c4bb95b-588e-4afd-824a-308462440a5c)


There is also aneat config.pl file with many customization settings:
And my favourite: 

```config{config_script} = "script.sh, script2.sh";``` 

And if you're a qemu user, you know how crazy you can go in scripting. 






