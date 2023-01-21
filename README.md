# NetPractice
* 42 Core Curriculum - Level 4
* Level 4 in the Holy Graph<br>
* Passed with 100% on 21st Jan 2023.<br>

<details>
  <summary>Level 6</summary>
  
  1. Erase all the modifiable fields (start with a clean sheet).<br>
  2. All the destinations of the routing tables should be filled in with : `0.0.0.0/0`<br>
  3. Copy the mask of R1 into the one of A1 (the same mask is used inside a subnetwork) : `255.255.255.128`<br>
  4. Choose any suitable IP for R1 between 128 and 255 (128 and 255 excluded) because the mask last byte is 128 (see CIDR Table) : `110.6.3.226` for instance<br>
  5. Copy the IP of R1 into the next hop of the forwarding table of A :`110.6.3.226`<br>
  6. Choose the network address and mask for the destination of the routing table of the Internet by make sure the IP adresses of R1 and A1 will be covered : `110.6.3.226/30` or `110.6.3.0/25` will work<br>
  
  ![NetPractive_Level_6](https://user-images.githubusercontent.com/107719618/213868500-84b71208-e565-4aff-83f1-31e216d8cd50.png)

  
  
</details>

<details>
  #<summary>Level 7</summary>
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
