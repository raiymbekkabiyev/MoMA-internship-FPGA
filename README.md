# Acceleration of Fully Homomorphic Encryption using Intel Arria Acceleration Cards

Keynotes: FPGA, Fully Homomorphic Encryption, Intel Arria Acceleration Cards

## Description: 
This research looks into Fully Homomorphic Encryption (FHE) which is a relatively new technology dedicated to provide absolute confidentiality for a user while using third party cloud-based servers. FHE is promising technology that allows manipulation on encrypted data without revealing private data. However, FHE is computationally heavy and thus slow process. This research project aims to accelerate these computations (addition and multiplication) using Intel Arria Acceleration Cards. 


## The following are my notes on some important concepts in FHE

### The notion of 'Noise' 
Let's suppose we have some message 'X' and we encrpt it --> Enc(X). There must be some randomness (noise) otherwise 'X' can be recovered with a dictionary attack! It is imporant to keep this noise under certain boundary for the owner of the secret key to be able to recover 'X'. Otherwise we loose consistency of the computation. The more FHE you do the more noise is there (noise accumulates over time). Noise growth is exponentional. 
How to solve this? Bootstrapping 
In simple terms: 
Let's say we encrypt message 'X' under secret key (K1) with certain noise. We do some operations on this Enc(X) and end up having some 'Y' with a new level of noise. Suppose at this point the level of noise is at maximum acceptible level. No if we perform any operations on 'Y' we will loose consistency due to high level of noise. So what we can do is we can encrypt our result 'Y' under a different key (K2), essentially creating one more layer over it. This encrypted text will have a new noise but in a acceptable range. At this point we have two keys: K1 and K2 where K1 is also encrypted under K2. Now we can perform decryption circuit homomorphically: K1 will be removed and we will end up with text 'Y' under K2 with redused noise. This is what bootstraping does but once again it is a slow process. 


## Isolated I/O and Memory Mapped I/O
Reference: https://technobyte.org/difference-memory-mapped-io-mapped-io/ 
In I/O mapped I/O or isolated I/O mapping, the I/O devices are given a separate addressing region. Separate from what? Separate from the memory. These separate address spaces are known as ‘Ports’.
