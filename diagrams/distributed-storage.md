graph TB

subgraph Record
  publicKey(Public Key)
  privateKey(Private Key)
  metadata(Metadata)
  attachments(Attachments)
  data(Record Data)
end

data-->payloads
attachments-->payloads

subgraph MetaStore
  publicKeyHash(PublicKey Hash - Address)
  signature(Signature)
  metadataJSON(Metadata JSON)
  payloadHashes(Payload Hashes)
  recordHash(Record Hash)
end

publicKey-->publicKeyHash

metadata-->metadataJSON

metadataJSON-->recordHash
payloadHashes-->recordHash

privateKey-->signature
recordHash-->signature

subgraph DataStore
  payloads(Record Payloads)
  payloadHash(Payload Hash)
end

payloadHash-->payloadHashes

payloads-->payloadHash
