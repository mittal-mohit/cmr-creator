# URL Shortener Architecture

```mermaid
graph TD
    subgraph Read Path (High Traffic)
        R_User[👤 User] -->|1. GET /g5| R_LB(Load Balancer)
        R_LB -->|2. GET /g5| R_API(URL Shortener Service)
        R_API -->|3. Get key 'g5'| R_Cache(Cache <br> e.g., Redis)
        R_Cache -- Cache Hit -->|4a. Returns long_url| R_API
        R_Cache -- Cache Miss -->|4b. Get key 'g5'| R_DB(NoSQL DB <br> e.g., DynamoDB)
        R_DB -->|5. Returns long_url| R_API
        R_API -->|6. Cache long_url| R_Cache
        R_API -->|7. HTTP 301 Redirect| R_User
    end

    subgraph Write Path (Lower Traffic)
        W_User[👤 User] -->|1. POST /urls| W_LB(Load Balancer)
        W_LB -->|2. long_url| W_API(URL Shortener Service)
        W_API -->|3. Request New ID| ID_Service(Unique ID Service <br> e.g., Snowflake)
        ID_Service -->|4. Returns unique_id (e.g., 1001)| W_API
        W_API -->|5. Base62 Encode| W_API
        W_API -->|6. Store 'g5':long_url| W_DB(NoSQL DB)
        W_DB -->|7. Success| W_API
        W_API -->|8. Returns 'x.co/g5'| W_User
    end

    style R_Cache fill:#f9f,stroke:#333,stroke-width:2px
    style ID_Service fill:#ccf,stroke:#333,stroke-width:2px
```

## Architecture Overview

This diagram illustrates a URL shortener service with two main operational paths:

### Read Path (High Traffic)
- **Purpose**: Handle URL redirections when users click short URLs
- **Flow**: User → Load Balancer → URL Service → Cache → Database (if cache miss) → Redirect
- **Key Components**: Cache (Redis) for fast lookups, NoSQL database (DynamoDB) for persistence

### Write Path (Lower Traffic)
- **Purpose**: Create new short URLs from long URLs
- **Flow**: User → Load Balancer → URL Service → ID Service → Encoding → Database Storage
- **Key Components**: Unique ID Service (Snowflake) for generating IDs, Base62 encoding for URL-friendly strings

### Performance Optimizations
- **Cache Layer**: Redis provides sub-millisecond response times for frequent lookups
- **Load Balancing**: Distributes traffic across multiple service instances
- **Separate Paths**: Read and write operations are optimized independently