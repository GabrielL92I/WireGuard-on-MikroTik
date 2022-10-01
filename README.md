# WireGuard on MikroTik v7 RouterOS only by Gabriel Lami
Configure WireGuard VPN on MikroTik

1- Firstly, we create WireGuard interface, the peer and the IP address network for the clients

 - WireGuard interface creation `WireGuard->Create new interface`
  
   Just create and click OK. No need to add something in this phase.
   ![wireguardinterface](https://user-images.githubusercontent.com/44748406/193423738-5d5333f2-b3d9-4d78-a91f-3eda3dc83a6f.png)
   
 - Network IP address creation. `IP->Address`
   
   You can choose whatever range you want. I will use this range `192.168.100.0/24`.
   ![address](https://user-images.githubusercontent.com/44748406/193423902-dff0c55e-2564-4c60-a982-3bd18b71a3ed.png)
   
 - Peer creation
 
 Public Key: You have to copy here the Publick Key found on the client WireGuard when you create the connection. For more check the last photo.
 Allowed Address: The IP that you want to give to the peer.
 ![peer](https://user-images.githubusercontent.com/44748406/193424666-3a0666cf-120b-4ffd-9618-b7cf1e275716.png)
