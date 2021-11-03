# An improved versionn of ERC721

ERC721 is the implementation of a standard API for NFTs within smart contracts. It provides basic functionality to track and transfer NFTs.

The implementation of EIP721 provided in OpenZeppelin works great, except for one fact that only token URI is stored on-chain, and there is no guarantee that the content itself would not be changed by malicious user.

One probable solution is to "leverage IPFS to store the tokenURI information", however this then dictates the storage method, which may proves to be inflexible in some situations.

Another solution, which is proposed and demonstrated in this project, is to store a hash of the file content in the smart contracts. Any modification to the file content, may be it text, audio, video, artistic creation, will change the hash of the content, and therefore makes the token invalid.

