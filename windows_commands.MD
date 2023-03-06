## Create Remote Desktop User by using command prompt:
````sh
net user Chaitanya.Lanka Chaitanya@123 /add
net localgroup "Remote Desktop Users" Chaitanya.Lanka /add
````
