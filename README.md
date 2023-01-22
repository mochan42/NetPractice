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
  #<summary>Level 8</summary>
</details>

<details>
  #<summary>Level 9</summary>
</details>

<details>
  #<summary>Level 10</summary>
</details>
