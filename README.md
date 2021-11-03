# An improved versionn of ERC721

ERC721 is the implementation of a standard API for NFTs within smart contracts. It provides basic functionality to track and transfer NFTs.

The implementation of EIP721 provided in OpenZeppelin works great, except for one fact that only token URI is stored on-chain, and there is no guarantee that the content itself would not be changed by malicious user.

One probable solution is to "leverage IPFS to store the tokenURI information", however this then dictates the storage method, which may proves to be inflexible in some situations.

Another solution, which is proposed and demonstrated in this project, is to store a hash of the file content in the smart contracts. Any modification to the file content, may be it text, audio, video, artistic creation, will change the hash of the content, and therefore makes the token invalid.

In EIP721, Creation of NFTs (“minting”) and destruction of NFTs (“burning”) is not included in the specification. Therefore, the mint and burn functions can be modified to incorporate the content hashes as a function paramter.

A mapping storage variable is added, which provides th mapping from token ID to content hash. When minting a token, besides receiver address and tokenId, a third parameter is provided, which stands for the content hash of the file the token is referring to. Accordingly, when burning a token, the content hash is deleted from the mapping.

Two functions are added to the contract: getContentHash(uint256 tokenId) and checkContentValidity(uint256 tokenId, bytes32 contenthash).

