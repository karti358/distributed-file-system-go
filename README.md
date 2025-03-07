# distributed-file-system-go

## Authors

- [@karti358](https://github.com/karti358)

---

### Distributed File System in Golang

#### Overview
This project implements a distributed file system using the Go programming language (Golang). The system is designed to facilitate the storage, retrieval, and sharing of files across multiple peers in a network. It leverages TCP connections for reliable data transmission and employs a peer-to-peer architecture to ensure that files can be accessed and transferred efficiently between nodes.

#### Key Features
1. **TCP Handshake and Connections**:
   - The system establishes TCP connections between peers using a standard TCP handshake process. This ensures a reliable and ordered communication channel for data transfer.
   - Each peer in the network can initiate and accept TCP connections, allowing for flexible and dynamic interactions.

2. **Data Encoding and Decoding**:
   - Data to be transmitted over the network is encoded to ensure integrity and compatibility. This may involve serialization techniques such as JSON or Protocol Buffers.
   - Upon receiving data, peers decode the information to retrieve the original file content or metadata.

3. **Peer-to-Peer Connections**:
   - The system employs a peer-to-peer (P2P) architecture, where each peer can act as both a client and a server.
   - Peers can discover and connect to other peers in the network, facilitating decentralized file sharing.

4. **File Transfer Mechanism**:
   - If a peer requests a file, the system checks if any other peer in the network has the requested file.
   - The file can be transferred directly from one peer to another, either to the requesting peer or to any other specified peer.
   - This mechanism ensures efficient use of network resources and reduces the load on any single node.

5. **Data Integrity and Reliability**:
   - The system ensures data integrity during transmission by using checksums or other verification methods.
   - Reliable data transfer is achieved through TCP, which handles packet loss, retransmission, and ordering.

#### Implementation Details
1. **TCP Handshake**:
   - The TCP handshake involves a three-step process: SYN, SYN-ACK, and ACK. This establishes a connection between two peers before any data is exchanged.

2. **Connection Management**:
   - Each peer maintains a list of active connections to other peers.
   - Connection management includes handling new connections, closing inactive connections, and reconnecting to peers as needed.

3. **Data Encoding/Decoding**:
   - Data is encoded using a chosen serialization format (e.g., JSON, Protocol Buffers) before being sent over the network.
   - Upon receipt, the data is decoded back into its original format for processing.

4. **File Storage and Retrieval**:
   - Files are stored locally on each peer's filesystem.
   - Metadata about available files is shared among peers to facilitate discovery and retrieval.

5. **Peer Discovery**:
   - Peers can discover each other using a bootstrap node or through a decentralized discovery protocol.
   - Once discovered, peers can establish direct connections for file transfer.

6. **File Transfer Protocol**:
   - The file transfer protocol includes commands for requesting files, sending files, and acknowledging receipt.
   - Data is sent in chunks to handle large files and ensure efficient transmission.

#### Use Cases
- **Distributed Backup**: Peers can back up files to multiple nodes, ensuring redundancy and fault tolerance.
- **File Sharing**: Users can share files directly with each other without relying on a central server.
- **Collaborative Work**: Teams can work on shared files, with changes propagated across peers in real-time.

## Tech Stack

- Golang, TCP, P2P

## Run Locally
Initialize git

```bash
git init
```

Clone the project

```bash
git clone https://github.com/karti358/distributed-file-system-go.git
```

enter the project directory

```bash
cd distributed-file-system-go
```

Build the project locally

```bash
make build
```

Run the project
```bash
make run
```

## Repository structure

```
├── p2p
│   ├── encoding.go
│   ├── handshake.go 
│   ├── message.go
│   ├── tcp_transport.go
│   ├── tcp_transport_test.go
│   ├── transport.go
│
├── .gitignore
├── LICENSE
├── Makefile
├── README.md
├── crypto.go
├── crypto_test.go
├── go.mod
├── go.sum
├── main.go
```
