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


2- Secondly, we will create firewall rule needed to allow peer connection. `IP->Firewall`

 - Firewall rule before the drop rule

   -Chain: input
   -Src. Address: 192.168.100.0/24
   -Action: Accept
   
   -Chain: input
   -Protocol: UDP
   -Dst. Port: 13231
   -Action: Accept

 ![firewall](https://user-images.githubusercontent.com/44748406/193424793-026d6e1e-db24-46a0-b1d9-cf0123e00a1a.png)
 
 
3- Finally, we create the VPN connection on the peer device(in this case is through an iPhone)

 - VPN Connection on iPhone
   
   INTERFACE
   Name: Whatever name here
   Public Key: Automatically generated(with green color). You have to use this key in the MikroTik peer public key
   Addresses: 192.168.100.2/32(same as the peer creation in MikroTik)
   Listen port: Generated automatically
   DNS servers: add your own
   
   PEER
   Public Key: You can find it on the MikroTik WireGuard interface you created earlier(red color)
   Endpoint: Your public IP:13231
   Allowed IPs: 0.0.0.0/0 
   
   ![unnamed](https://user-images.githubusercontent.com/44748406/193425016-c7a7af00-7f80-400b-a7ef-c4d012c1aa55.jpg)
   
   Good job, you are now connected!
   
   Thank you.
