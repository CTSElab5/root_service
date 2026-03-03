# Microservices System - E-Commerce Platform

A complete microservices-based e-commerce system built with Spring Boot, Docker, and API Gateway pattern.

## Project Overview

This project implements a microservices architecture with the following services:
- **API Gateway** - Routes requests to appropriate microservices (Port 8086)
- **Item Service** - Manages product catalog (Port 8081)
- **Order Service** - Handles customer orders (Port 8082)
- **Payment Service** - Processes payments (Port 8083)

## Architecture

```
                    ┌─────────────────┐
                    │   API Gateway   │
                    │   (Port 8086)   │
                    └────────┬────────┘
                             │
          ┌──────────────────┼──────────────────┐
          │                  │                  │
    ┌─────▼─────┐     ┌─────▼─────┐     ┌─────▼─────┐
    │   Item    │     │   Order   │     │  Payment  │
    │  Service  │     │  Service  │     │  Service  │
    │ Port 8081 │     │ Port 8082 │     │ Port 8083 │
    └───────────┘     └───────────┘     └───────────┘
```

## Quick Start

### Prerequisites
- Docker Desktop installed and running
- Git
- Java 17+ (for local development)
- Maven (for local development)

### Running with Docker

1. **Clone the repository with submodules:**
   ```bash
   git clone --recursive https://github.com/CTSElab5/root_service.git
   cd root_service
   ```

2. **Build all services:**
   ```bash
   docker-compose build
   ```

3. **Start all services:**
   ```bash
   docker-compose up
   ```

4. **Access the services:**
   - API Gateway: http://localhost:8086
   - Item Service (direct): http://localhost:8081
   - Order Service (direct): http://localhost:8082
   - Payment Service (direct): http://localhost:8083

### Stopping Services
```bash
docker-compose down
```

## API Endpoints

### Item Service (/items)

#### Get All Items
```http
GET http://localhost:8086/items
```

#### Add New Item
```http
POST http://localhost:8086/items
Content-Type: application/json

{
  "name": "Laptop"
}
```

#### Get Item by ID
```http
GET http://localhost:8086/items/1
```

### Order Service (/orders)

#### Get All Orders
```http
GET http://localhost:8086/orders
```

#### Place New Order
```http
POST http://localhost:8086/orders
Content-Type: application/json

{
  "item": "Laptop",
  "quantity": 2,
  "customerId": "C001"
}
```

#### Get Order by ID
```http
GET http://localhost:8086/orders/1
```

### Payment Service (/payments)

#### Get All Payments
```http
GET http://localhost:8086/payments
```

#### Process Payment
```http
POST http://localhost:8086/payments/process
Content-Type: application/json

{
  "orderId": 1,
  "amount": 1299.99,
  "method": "CARD"
}
```

#### Get Payment by ID
```http
GET http://localhost:8086/payments/1
```

## Technology Stack

- **Framework:** Spring Boot 3.x
- **Language:** Java 17
- **API Gateway:** Spring Cloud Gateway
- **Containerization:** Docker & Docker Compose
- **Build Tool:** Maven
- **Architecture:** Microservices

## Project Structure

```
microservice_ctse/
├── docker-compose.yml          # Docker orchestration configuration
├── gateway2/                   # API Gateway service
│   ├── src/
│   ├── pom.xml
│   └── dockerfile
├── item/                       # Item microservice
│   ├── src/
│   ├── pom.xml
│   └── dockerfile
├── order/                      # Order microservice
│   ├── src/
│   ├── pom.xml
│   └── dockerfile
└── payment2/                   # Payment microservice
    ├── src/
    ├── pom.xml
    └── dockerfile
```

## Testing

### Manual Testing with cURL

**Test Item Service:**
```bash
# Get all items
curl http://localhost:8086/items

# Add new item
curl -X POST http://localhost:8086/items \
  -H "Content-Type: application/json" \
  -d '{"name":"Headphones"}'
```

**Test Order Service:**
```bash
# Place order
curl -X POST http://localhost:8086/orders \
  -H "Content-Type: application/json" \
  -d '{"item":"Laptop","quantity":2,"customerId":"C001"}'
```

**Test Payment Service:**
```bash
# Process payment
curl -X POST http://localhost:8086/payments/process \
  -H "Content-Type: application/json" \
  -d '{"orderId":1,"amount":1299.99,"method":"CARD"}'
```

### Testing with Postman

Import the `Microservices_API_Tests.postman_collection.json` file into Postman to run all API tests.

See `API_TESTING_EVIDENCE.md` for detailed testing documentation with screenshots.

## Docker Configuration

### Individual Service Ports
- API Gateway: 8086
- Item Service: 8081
- Order Service: 8082
- Payment Service: 8083

### Network
All services run on a bridge network called `microservices-net` for inter-service communication.

## Development Setup

### Building Individual Services

**Item Service:**
```bash
cd item
mvn clean package -DskipTests
```

**Order Service:**
```bash
cd order
mvn clean package -DskipTests
```

**Payment Service:**
```bash
cd payment2
mvn clean package -DskipTests
```

**Gateway:**
```bash
cd gateway2
mvn clean package -DskipTests
```

## Repository Links

- **Main Repository:** https://github.com/CTSElab5/root_service.git
- **Gateway Service:** https://github.com/CTSElab5/gateway_Service.git
- **Item Service:** https://github.com/CTSElab5/item_Service.git
- **Order Service:** https://github.com/CTSElab5/order_Service.git
- **Payment Service:** https://github.com/CTSElab5/payment_service.git

## Team

CTSElab5

## License

This project is developed for educational purposes.

## Additional Documentation

- [API Testing Evidence](API_TESTING_EVIDENCE.md)
- [Postman Collection](Microservices_API_Tests.postman_collection.json)

---

**Last Updated:** March 3, 2026
