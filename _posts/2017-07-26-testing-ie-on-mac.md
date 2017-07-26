---
title:        "Testing IE on Mac"
description:  "From time to time I need to test my angular apps in IE - this is a short guide on how to setup IE on Mac"
author:       "Martin"
---

From time to time I need to test Angular apps on Internet Explorer. This is a short introduction on how to setup a virtual machine with Internet Explorer and develop on your host machine (in my case a Mac, but maybe this would also work for other unix machines).

First you need to [download VirtualBox](https://www.virtualbox.org/wiki/Downloads) if not installed yet.

Next step is to go to [developer.microsoft.com](https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/) and select a virtual machine that includes your needed IE version. As aplatform please select VirtualBox and download the zip file (Attention this file is alomst 5 GB big, don't do this on mobile).

Unzip the VM you downloaded and copy the folder to a permanent place. After that open VirtualBox by clicking on the **\*.ovf** file.

Spin up the VM and open notepad as administrator (the password is given on the Microsoft page; to open notepad search and right click on the notepad icon - for those like me who didn't use Windows in ages). In your notepad you need to open the following file `C:\windows\system32\drivers\etc\hosts` and add 

```
10.0.2.2   outer
```  
to the end of the file. This will pipe all request to http://10.0.2.2 to your local machine (in my case my Mac).

When you start your angular webserver you have to add a special flag, so the webpack webserver will not block http://10.0.2.2 

```
ng serve --disable-host-check
```

Now you are able to look at your Angular app in the VM's IE by browsing to [http://10.0.2.2:4200](http://10.0.2.2:4200).

Microsoft suggests to create a snapshot, because the license for the VM is only 90 days vaild. So I would recommend to do the snahpshort right now, when everything worked.