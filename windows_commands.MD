#### Create Remote Desktop User by using command prompt:
````sh
net user user_name user_passwd /add
net localgroup "Remote Desktop Users" user_name /add
````
## Extend Volume on existing instance:
#### Get volume ID
````sh
get-disk
````
#### modify volume on aws console
![image](https://user-images.githubusercontent.com/48147995/223010867-5c2e3ab2-59e8-4f42-8757-394fa9449cfa.png)

#### login to client machine to extend the existing volume
````sh
click windows --> computer management --> disk management --> action (top left) --> rescan disk
````
![image](https://user-images.githubusercontent.com/48147995/223011595-9d98ad0d-eb16-4306-a02a-6a8928e17c9f.png)

#### Select existing volume and extend volume like below and do next next apply.
![image](https://user-images.githubusercontent.com/48147995/223011849-0f29eb40-ebf5-40df-a40d-7ecb137242cb.png)

