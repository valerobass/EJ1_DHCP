```mermaid
sequenceDiagram
    participant Server1
    participant Client
    participant Server2

    note over Client: The client boot the computer and send a broadcast
    Client->>+Server1: DhcpDiscovery
    Client->>+Server2: DhcpDiscovery
    Server1-->>-Client: DhcpOffer
    Server2-->>-Client: DhcpOffer
    Client->>+Server1: DhcpRequest
    Client->>+Server2: DhcpRequest
    Server1-->>-Client: DhcpPack
    note over Client: There is an outage. After 3 minutes try no connnect again
    Client->>+Server1: DhcpRequest
    Client->>+Server1: DhcpRequest
    note over Client: The server1 doesn´t respond
    Client->>+Server2: DhcpDiscovery
    Server2-->>-Client: DhcpOffer
    Client->>+Server2: DhcpRequest
    Server2-->>-Client: DhcpPack
    note over Client: At 50% of the lease answer at server If the ip is still available
    note over Client: After 8 hours of use the lease time is over an try to connect again with the server
    Client->>+Server1: DhcpDiscovery
    Client->>+Server2: DhcpDiscovery
    Server1-->>-Client: DhcpOffer
    Server2-->>-Client: DhcpOffer
    Client->>+Server1: DhcpRequest
    Client->>+Server2: DhcpRequest
    Server1-->>-Client: DhcpPack
    note over Client: At 50% of the lease answer at server If the ip is still available
    note over Client: The client send a DhcpRequest and the server confirm the ip is still available
    note over Client: The user turn OFF the PC for 1 hour
    note over Client: The user turn ON the PC
    Client->>+Server1: DhcpDiscovery
    Client->>+Server2: DhcpDiscovery
    Server1-->>-Client: DhcpOffer
    Server2-->>-Client: DhcpOffer
    Client->>+Server1: DhcpRequest
    Client->>+Server2: DhcpRequest
    Server2-->>-Client: DhcpPack
    note over Client: The user turn OFF the PC```