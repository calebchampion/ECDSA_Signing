# Address Explorer
## Understanding bitcoin addresses in the P2WPKH form
1. Creates or uses **BIP39 seed phrase** from 256 bit entropy, or other way around.
2. Calculates 64 byte **root seed** with 2048 iterations of PBKDF2-HMAC-SHA512 using seed phrase and salt for (**passphrase**).
3. Uses HMAC-SHA512 to hash the root seed to calulate the 64 byte **parent extended private key(master extended private key)** by adding the first 32 bytes **parent private key** and the last 32 bytes **chain code** from the HMAC-SHA512 hash to be used for the BIP32 Hierarchical Deterministic children keys later.  The chain code will be used to construct the child keys.
4. Used the **parent private key** and ECDSA to solve for the compressed (& uncompressed) **public key**, then adding that with the chain code to calculate the **parent extended public key(master extended public key)**.
5. Create private, public, and addresses for **child addresses** for **hardened** & **normal**
**Need to describe how child addresses & priv keys are made**

### Directions
Need to download "english" file as it is the bip39 wordlist used for conversion.  Just change "english" to the file path and name.

    $ pip install pandas as pd
    $ pip install hashlib
    $ pip install hmac
    $ pip install binascii
    $ pip install ecdsa
