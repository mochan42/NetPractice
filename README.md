# NetPractice
* 42 Core Curriculum - Level 4
* Level 4 in the Holy Graph<br>
* Passed with 100% on 21st Jan 2023.<br>

# CIDR Table
The CIDR notation is another way to write the Net mask.<br>
What is important to remember for NetPractice is how many IP addresses are available for a given mask.<br>
`Number of Hosts = Number of IP Addresses - 2` since 1 address is reserved for the network address and another 1 address is reserved for the broadcast address.<br>

| CIDR mask notation | Number of IP Addresses | Number of Hosts | Net mask |
| --- | --- |--- | --- |
| /30 | 4 | 2 | 255.255.255.252 |
| /29 | 8 | 6 | 255.255.255.248 |
| /28 | 16 | 14 | 255.255.255.240 |
| /27 | 32| 30 | 255.255.255.224 |
| /26 | 64 | 62 | 255.255.255.192 |
| /25 | 128 | 126 | 255.255.255.128 |
| /24 | 256 | 254 | 255.255.255.0 |
| /18 | 16 384 | 16 382 | 255.255.192.0 |
| /16 | 65 536 | 65 534 | 255.255.0.0 |


<details>
  <summary>Level 6</summary>
  
  1. Erase all the modifiable fields (start with a clean sheet).<br>
  2. All the destinations of the routing tables should be filled in with : `0.0.0.0/0`<br>
  3. Copy the mask of R1 into the one of A1 (the same mask is used inside a subnetwork) : `255.255.255.128`<br>
  4. Choose any suitable IP for R1 between 128 and 255 (128 and 255 excluded) because the mask last byte is 128 (see CIDR Table) : `110.6.3.226` for instance<br>
  5. Copy the IP of R1 into the next hop of the forwarding table of A :`110.6.3.226`<br>
  6. Choose the network address and mask for the destination of the routing table of the Internet by make sure the IP adresses of R1 and A1 will be covered : `110.6.3.226/30` or `110.6.3.0/25` will work.<br>
  
  ![NetPractive_Level_6](https://user-images.githubusercontent.com/107719618/213868500-84b71208-e565-4aff-83f1-31e216d8cd50.png)

  
  
</details>

<details>
  <summary>Level 7</summary>
  
  1. Erase all the modifiable fields (start with a clean sheet).<br>
  2. All the destinations of the routing tables should be filled in with : `0.0.0.0/0`<br>
  3. We have 3 networks with only 2 IP address to assign so we can fill in the mask of A1, R11, R12, R21, R22 and C1 with : `255.255.255.252`<br>
  4. The next hop in the forwarding table of A is equal to the IP of the next router interface R11 : `107.198.14.1`<br>
  5. The IP address of A1 can only be : `107.198.14.2` since `107.198.14.1` is already used.<br>
  6. Since the IP address of R12 is `107.198.14.254`, then the next hop of the forwarding table of router R2 is : `107.198.14.254`<br>
  7. The IP address of the R21 can only be : `107.198.14.253` since `107.198.14.254` is already used.<br>
  8. Since the IP address of R21 is `107.198.14.253`, then the next hop of the forwarding table of router R1 is : `107.198.14.253`<br>
  9. For network R22 - C1, we need to find what IP addresses are available in 107.198.14.xxx format : <br>
  &emsp;&emsp;&emsp; * Due to network R11 - A1, the IP addresses `107.198.14.xxx` with `xxx` ranging from `000` to `003` included are used.<br>
  &emsp;&emsp;&emsp; * Due to network R12 - R21, the IP addresses `107.198.14.xxx` with `xxx` ranging from `252` to `255` included are used.<br>
  Hence, the IP addresses available are `107.198.14.004` to `107.198.14.251` : for simplicity, we will use addresses from `107.198.14.004` to `107.198.14.007`, therefore : <br>
  &emsp;&emsp;&emsp; * IP address of R22 is `107.198.14.005`<br>
  &emsp;&emsp;&emsp; * IP address of C is `107.198.14.006`<br>
  &emsp;&emsp;&emsp; * Next hop of forwarding table of C is `107.198.14.005`<br>

  
  ![NetPractive_Level_7](https://user-images.githubusercontent.com/107719618/213916288-f1636f84-c3d9-4355-9a33-4d2b49024965.png)

  
  
</details>

<details>
  <summary>Level 8</summary>
  
  1. Erase all the modifiable fields (start with a clean sheet).<br>
  2. All the destinations of the routing tables should be filled in with : `0.0.0.0/0`<br>
  3. The next hop of the forwarding table of the Internet I should be equal to the IP address of the interface R12 of router R1 : `163.178.250.12`<br>
  4. For network R23 - D1, the mask of D1 and R23 must be be identical so the mask of R23 is : `255.255.255.240`.<br>
  5. For networks R13 - R21 and R22 - C1, there are only 2 IP addresses to assign in each network so we can use the following mask for R13, R21, R22 and C1 : `255.255.255.252`.<br>
  6. From the network R12 - Internet, the 16 IP addresses `163.178.250.0` to `163.178.250.15` are reserved because the mask is `255.255.255.240` and we know one of the IP address already in use R12 is `163.178.250.12`. <br>
  7. The forwarding table of router R2 assign the next hop to IP address `164.153.247.62`so IP address of R13 must be `164.153.247.62`. This means the network R13 - R21 will use the IP addresse from `164.153.247.60` to `164.153.247.63` included.
  8. As a consequence, the only choice possible for the IP address of R21 is `164.153.247.61`<br>
  9. For network R23 - D1, 16 IP addresses will be reserved because the mask is `255.255.255.240`. Among the remaining available IP addresses in `164.153.247.xxx`, we can choose `xxx` from `16` to `31` included, so :<br>
  &emsp;&emsp;&emsp; * IP address of R23 is `164.153.247.17`<br>
  &emsp;&emsp;&emsp; * IP address of D1 is `164.153.247.18`<br>
  &emsp;&emsp;&emsp; * next hop of the forwarding table of D1 is `164.153.247.17`<br>
  10. For network R22 - C1, 4 IP addresses will be reserved because the mask is `255.255.255.252`. Among the remaining available IP addresses in `164.153.247.xxx`, we can choose `xxx` from `32` to `35` included, so :<br>
  &emsp;&emsp;&emsp; * IP address of R23 is `164.153.247.33`<br>
  &emsp;&emsp;&emsp; * IP address of D1 is `164.153.247.34`<br>
  &emsp;&emsp;&emsp; * next hop of the forwarding table of D1 is `164.153.247.33`<br>
  11. 1st Next hop of the forwarding table of router R1 should be the IP adress of R21 : `164.153.247.61`<br>
  
  
  
  ![NetPractive_Level_8_Part_1](https://user-images.githubusercontent.com/107719618/213920462-3521dc19-b456-4726-a8b5-c3a311bb8c34.png)
  ![NetPractive_Level_8_Part_2](https://user-images.githubusercontent.com/107719618/213920465-6e319eb8-6790-43c0-957b-757e7f8baefd.png)

  
  
</details>

<details>
  <summary>Level 9</summary>
  
  1. Erase all the modifiable fields (start with a clean sheet).<br>
  2. All the destinations of the routing tables should be filled in with : `0.0.0.0/0` except the first destination of the router R1 and the two first destinations of the routing table of the Internet.<br>
  3. The mask of R13 should be identical to R21 : `255.255.255.252`<br>
  4. The mask of A1 and B1 should be identical to R11 : `255.255.255.128`<br>
  5. The mask of D1 should be identical to R23 : `/18`<br>
  6. Since the next hop of forwarding table D is : `91.118.249.193`, then the IP address of R23 is `91.118.249.193`.<br>
  7. Therefore, a possible ID address for D1 is : `91.118.249.194`<br>
  8. For network R22 - C1, we only need to assign 2 IP addresses, so we can choose the following mask : `255.255.255.252`<br>
  9. From the network R12 - Internet, the 16 IP addresses `163.172.250.0` to `163.172.250.15` are reserved because the mask is `255.255.255.240` and we know one of the IP address R12 already in use is `163.178.250.12`. <br>
  10. For network R13 - R21, we can use the following adresses `163.172.250.xxx` with `xxx` ranging from `16` to `255`. Let's use `163.172.250.16` to `163.172.250.19`. Therefore:<br>
  &emsp;&emsp;&emsp; * IP address of R13 is `163.172.250.17`<br>
  &emsp;&emsp;&emsp; * IP address of R21 is `163.172.250.18`<br>
  &emsp;&emsp;&emsp; * IP address of next hop of router R2 is `163.172.250.17`<br>
  11. For network R22 - C1, we can use the following adresses `163.172.250.xxx` with `xxx` ranging from `20` to `255`. Let's use `163.172.250.20` to `163.172.250.23`. Therefore:<br>
  &emsp;&emsp;&emsp; * IP address of R22 is `163.172.250.21`<br>
  &emsp;&emsp;&emsp; * IP address of C1 is `163.172.250.22`<br>
  &emsp;&emsp;&emsp; * IP address of next hop of forwarding table of C is `163.172.250.21`<br>
  12. For network R11 - A1 - B1, we can use the following adresses `163.172.250.xxx` with `xxx` ranging from `24` to `255`. Let's use `163.172.250.128` to `163.172.250.255` since the mask 255.255.255.128 imposes to reserve 128 IP addresses. Therefore:<br>
  &emsp;&emsp;&emsp; * IP address of R11 is `163.172.250.129`<br>
  &emsp;&emsp;&emsp; * IP address of B1 is `163.172.250.130`<br>
  &emsp;&emsp;&emsp; * IP address of A1 is `163.172.250.131`<br>
  &emsp;&emsp;&emsp; * IP address of next hop of forwarding table of B and A is `163.172.250.129`<br>
  13. For routing table of router R1 :<br>
  &emsp;&emsp;&emsp; * The 1st destination is the network address of network R22 - C2 : `163.172.250.20/30`<br>
  &emsp;&emsp;&emsp; * The 2nd destination is default : `0.0.0.0/0`<br>
  &emsp;&emsp;&emsp; * The 1st next hop is the IP address of R21 : `163.172.250.18`<br>
  &emsp;&emsp;&emsp; * The 2nd next hop is the IP address of R21 : `163.172.250.18`<br>
  14. For routing table of the Internet :<br>
  &emsp;&emsp;&emsp; * The 1st destination is the network address of B : `163.172.250.20/30`<br>
  &emsp;&emsp;&emsp; * The 2nd destination is the network address of A : `163.172.250.128/25`<br>
  &emsp;&emsp;&emsp; * The 3rd destination is default : `0.0.0.0/0`<br>
  
  ![NetPractive_Level_9_Part_1](https://user-images.githubusercontent.com/107719618/213923643-9cbb5103-d630-4f30-a6ba-934455bdc890.png)
  ![NetPractive_Level_9_Part_2](https://user-images.githubusercontent.com/107719618/213923649-0dcfef4e-bce5-4f4f-a127-bc5af577d44e.png)
  ![NetPractive_Level_9_Part_3](https://user-images.githubusercontent.com/107719618/213923655-39110208-65ff-4c2a-b7db-e011669bc3a1.png)

</details>

<details>
  <summary>Level 10</summary>
  
  1. Erase all the modifiable fields (start with a clean sheet).<br>
  2. All the destinations of the routing tables should be filled in with : `0.0.0.0/0` except the first destination of the router R1.<br>
  3. The masks of H11 and H21 must be identical to R11 : `255.255.255.128` <br>
  4. The mask of R13 must be identical to the mask of R21 : `255.255.255.252`. This network R13 - R21 reserves all IP addresses `130.121.1.xxx` with `xxx`ranging from `252` to `255`. <br>
  5. The mask of R23 must be identical to the mask of H41 : `255.255.255.192` <br>
  6. For network R22 - H31, we only need to assign 2 IP addresses so the mask `255.255.255.252` will be enough. 
  7. For network R11 - H11 - H21, the mask is `255.255.255.128` and 1 of the IP is `130.121.1.1` so this network reserves all IP addresses `130.121.1.xxx` with `xxx`ranging from `0` to `127`. So a possible IP address for H21 is : `130.121.1.3` <br>
  8. IP address of R23 must be `130.121.1.129` because the next hop of forwarding table H4 is `130.121.1.129`. By the way, all IP addresses reserved from the network R23 - H41 are `130.121.1.128` to `130.121.1.191` because the mask is `255.255.255.192`.<br>
  9. For network R22 - H31, possible remaining IP addresses are `130.121.1.xxx` with `xxx` from `192` to `251`. Therefore :<br>
  &emsp;&emsp;&emsp; * A possible IP address for R22 is : `130.121.1.193`<br>
  &emsp;&emsp;&emsp; * A possible IP address for H31 is : `130.121.1.194`<br>
  &emsp;&emsp;&emsp; * The IP address for the next hop of forwarding table H3 is : `130.121.1.193`<br>
  10. 1st destination network address of router table of R1 is default : `0.0.0.0/0`<br>
  11. Destination network address of the internet must cover all IP of `130.121.1.xxx` with `xxx` from `0` to `255` so the network address is : `130.121.1.0/24`
  
  
  
  
  
  
  
</details>
