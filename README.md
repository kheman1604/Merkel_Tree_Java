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

## 3. Algorithm & Steps
There are Various Functions Available in a Merkel Tree Implementation, So We have an Algorithm for all the functions to be implemented.

### Algorithm of find function in Merkle tree
- Step 1: We will take tree and key as parameters.

- Step 2: If the tree is null then we will return null.

- Step 3: If the tree->key is equal to the key we will return the tree.

- Step 4: If the key is smaller than tree->key then we will return find(tree->left, key)

- Step 5: else return find(tree->right, key)

### Algorithm to add a node in Merkle tree.

- Step 1: We will take key and value as parameters.
- Step 2: Take the hash(key) and store it in a variable called index.
- Step 3: store (struct node*) arr[index].head in a pointer called tree of datatype node.
- Step 4: create a new node with its key as key and value as value and both links as null.
- Step 5: If the tree is null then assign the new node to the head and increment the size by 1.
- Step 6: If the tree is not null then we will check if the key is already present in the tree using the find function.
- Step 7: If the key is already present in the tree then we will update the value.
- Step 8: If it is not present in the tree then we will use the insert function to insert the element.

### Algorithm of insert function.

- Step 1: It will take tree and item pointers of node data type as parameters.
- Step 2: If item->key is smaller than tree->key and tree->left is null then assign the item to tree->left.
- Step 3: If item->key is smaller than tree->key and tree->left is not null then call insert function with tree->left and item as parameters.
- Step 4: If item->key is greater than tree->key and tree->right is null then assign the item to tree->right.
- Step 5: If item->key is greater than tree->key and tree->right is not null then call insert function with tree->right and item as parameters.

### Algorithm to delete a node in Merkle tree.

- Step 1: We will take a key as a parameter.
- Step 2: Take the hash(key) and store it in a variable called index.
- Step 3: store (struct node*) arr[index].head in a pointer called tree of datatype node.
- Step 4: If the tree is null then the key is not present.
- Step 5: If the tree is not null then we will check if the key is already present in the tree using the find function.
- Step 6: If the find function returns null then the key is not present in the tree.
- Step 7: If it is not null then we will use the remove function to delete the element.

### Algorithm of remove function.

- Step 1: It will take tree and key as parameters.
- Step 2: If the tree is null then return null.
- Step 3: If the key is smaller than the tree->key then tree->left is equal to remove(tree->left, key) and return tree.
- Step 4: If the key is greater than the tree->key then tree->right is equal to remove(tree->right, key) and return tree.
- Step 5: else if the tree->left is equal to null and the tree->right is equal to null then decrement the size and return tree->left.
- Step 6: else if the tree->left is not equal to null and the tree->right is equal to null then decrement the size and return tree->left.
- Step 7: else if tree->left is equal to null and tree->right is not equal to null then decrement the size and return tree->right.
- Step 8: else assign tree->left to a pointer called left of data type node.
- Step 9: While left->right is not equal to null, left is equal to left->right.
- Step 10: tree->key is equal to left->key.
- Step 11: tree->value is equal to left->value.
- Step 12: tree->left is equal to remove(tree->left, tree->key).
- Step 13: Return tree.

