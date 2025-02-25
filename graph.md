```mermaid
    graph LR
    A"net-a" -->|VPC Peering| B(Google-Owned VPC (Cloud Build Private Pool));
    A -->|VPC Peering| C(Google-Owned VPC (GKE Control Plane));
    D[Another VPC Network (net-b)] -->|VPC Peering| E[Yet Another VPC Network (net-c)];
    B--X No Connectivity --> C;
    D--X No Connectivity --> A;
    E--X No Connectivity --> A;
    subgraph Google Cloud
        B;
        C;
    end
    subgraph Your Project
        A;
        D;
        E;
    end

    style B fill:#f9f,stroke:#333,stroke-width:2px
    style C fill:#f9f,stroke:#333,stroke-width:2px

    style A fill:#ccf,stroke:#333,stroke-width:2px
    style D fill:#ccf,stroke:#333,stroke-width:2px
    style E fill:#ccf,stroke:#333,stroke-width:2px

    subgraph "VPC Network Peering Limitations"
        F[No Transitive Peering];
        G[Auto Mode VPC Restrictions];
    end
    F-->B;
    F-->C;
    G-->A;
    ```
