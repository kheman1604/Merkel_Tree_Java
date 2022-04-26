# Merkel Tree
## 1.  Introduction

A Merkle tree is a hash-based data structure that is a generalization of the hash list. It is a tree structure in which each leaf node is a hash of a block of data, and each non-leaf node is a hash of its children. Typically, Merkle trees have a branching factor of 2, meaning that each node has up to 2 children.

![image](https://user-images.githubusercontent.com/55325257/165240957-7769d22e-4534-4a0e-9a04-62bc5e6a27d3.png)

A hash function maps an input to a fixed output and this output is called hash.  The output is unique for every input, and this enables fingerprinting of data.  So, huge amounts of data can be easily identified through their hash. 
- This structure of the tree allows efficient mapping of huge data and small changes made to the data can be easily identified.
- If we want to know where data change has occurred, then we can check if data is consistent with root hash and we will not have to traverse the whole structure but only a small part of the structure.
- The root hash is used as the fingerprint for the entire data.

## 2. Architecture of Merkel Tree

In the blockchain, each block has a Merkle root stored in the block header. Merkle tree allows every node on the network to verify individual transaction without having to download and validate the entire block. If a copy of the block in the blockchain networks has the same Merkle root to another, then the transactions in that block are the same. Even a bit of incorrect data would lead to vastly different Merkle roots because of the properties of the hash. Therefore, it is not necessary to verify the amount of required information .

![image](https://user-images.githubusercontent.com/55325257/165241263-94c4d79a-d870-4b76-b5e6-757bd76782d8.png)

`Architecture of Merkel Tree`

![image](https://user-images.githubusercontent.com/55325257/165241324-836b3e9d-7bca-4467-8058-0e009efc2fef.png)

`Verification Mechanism in a Merkel Tree Transaction `
