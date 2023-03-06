## Create Remote Desktop User by using command prompt:
````sh
net user user_name user_passwd /add
net localgroup "Remote Desktop Users" user_name /add
````
