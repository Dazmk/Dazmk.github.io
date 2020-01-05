title: 配置开机自启rails以及chromium
author: Dashy
tags:
  - Rails
  - Raspberry Pi
categories:
  - Raspberry Pi
date: 2018-02-06 23:01:00
---
![image](http://p16vszsby.bkt.clouddn.com/stories_logo.svg?attname=&e=1517555769&token=NYX5b6QaVFGMB5vzHSgy0lp2jGcBlHXbg7YIca07:dVrK4uzv6s1E5ukGOGGRYGc4zqM)
# Stories Dashboard

To startup rails and chromium when the raspberry PI startup.  


![rails](https://img.shields.io/badge/rails-5.1.4-red.svg) ![ruby](https://img.shields.io/badge/ruby-2.5.0-blue.svg) ![created](https://img.shields.io/badge/created-Jan%202018-brightgreen.svg)

 1. **Clone repo**, open Terminal enter this code

> ```git clone git@github.com:namiwang/stories-dashboard.git```


 2. **Install gems**, run this lines of codes separately
 
> ```cd stories-dashboard```  
> ```bundle```

 3. **Change path**, if the path you choose don't like this ```/home/pi/workspace/stories-dashboard```, you must edit two files in stories-dashboard/app/bin 

- startup

    change  
    ~~```cd /home/pi/workspace/stories-dashboard```~~  
    into  
    ```cd /yourpath/stories-dashboard```

- rc.local

    change  
    ~~```su pi -c "exec /home/pi/workspace/stories-dashboard/bin/startup"```~~  
    into  
    ```su pi -c "exec /yourpath/stories-dashboard/bin/startup"```
 4. > ```reboot``` 

## Prohibited raspberry PI sleeping

1. Open Terminal enter this command
> ```sudo nano /etc/lightdm/lightdm.conf```

2. Press **"Ctrl + w"** to find ==[Seat:*]==, after this few lines you will see 
> ```# xserver-command=X```  

change it into  

> ```xserver-command = X -s 0 -dpms```  

it means to Close the screen saver and Display Power Management Signaling.

3. > ```reboot```
