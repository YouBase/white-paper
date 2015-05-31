graph TB

subgraph BIP-32 Node
  publicKey(Public Key)
  privateKey(Private Key)
  data(Data)
  links(Links)
end

links-->linksJSON

subgraph Document
  address(ID - Address)
  signature(Signature)
  dataJSON(Data)
  linksJSON(Links)
  documentHash(Revision - Document Hash)
end

publicKey-->address

data-->dataJSON

dataJSON-->documentHash
linksJSON-->documentHash

privateKey-->signature
documentHash-->signature

subgraph Link Storage
  linkHash(Hashed Link Data)
  linkData(Linked Data)
end

linkData-->linkHash

linkHash-->links
linkHash-->linksJSON
