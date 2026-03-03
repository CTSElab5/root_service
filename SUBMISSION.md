# Microservices System Project Submission

## Student/Team Information

---

## GitHub Repository Link

**Main Repository:** https://github.com/CTSElab5/root_service.git

### Repository Structure

The repository contains the complete microservices system with the following organization:

- **Main Repository (root_service):** Contains docker-compose configuration and orchestrates all submodules
- **Gateway Service:** https://github.com/CTSElab5/gateway_Service.git
- **Item Service:** https://github.com/CTSElab5/item_Service.git
- **Order Service:** https://github.com/CTSElab5/order_Service.git  
- **Payment Service:** https://github.com/CTSElab5/payment_service.git

---

## System Architecture

### Microservices Overview

Our system implements a complete e-commerce platform using microservices architecture with the following components:

1. **API Gateway (Port 8086)**
   - Routes all incoming requests to appropriate services
   - Implements Spring Cloud Gateway
   - Centralizes API access

2. **Item Service (Port 8081)**
   - Manages product catalog
   - CRUD operations for items
   - Pre-populated with sample data

3. **Order Service (Port 8082)**
   - Handles customer orders
   - Order creation and management
   - Tracks order status

4. **Payment Service (Port 8083)**
   - Processes payments
   - Links payments to orders
   - Supports multiple payment methods

### Technology Stack

- **Framework:** Spring Boot 3.x
- **Language:** Java 17
- **API Gateway:** Spring Cloud Gateway
- **Containerization:** Docker & Docker Compose
- **Build Tool:** Maven
- **Version Control:** Git with Submodules

---

## Docker Setup

### Docker Compose Configuration

The system uses Docker Compose for orchestration with the following setup:

```yaml
services:
  - item-service (Port 8081)
  - order-service (Port 8082)
  - payment-service (Port 8083)
  - api-gateway (Port 8086)
  
network:
  - microservices-net (bridge network)
```

### Building and Running

```bash
# Clone with submodules
git clone --recursive https://github.com/CTSElab5/root_service.git

# Build all services
docker-compose build

# Start all services
docker-compose up

# Stop services
docker-compose down
```

### Dockerfile Setup

Each service has its own Dockerfile with:
- Multi-stage build for optimization
- Java 17 runtime
- Exposed service ports
- Health checks

---

## API Testing Evidence

### Testing Methodology

Complete API testing was performed using:
- **Postman** for structured API testing
- **cURL** for command-line verification
- **Docker** for containerized deployment testing

### Test Coverage

| Service | Endpoints | Tests Conducted | Success Rate |
|---------|-----------|----------------|--------------|
| Item Service | 3 | 4 (including error handling) | 100% |
| Order Service | 3 | 4 (including validation) | 100% |
| Payment Service | 3 | 4 (including negative tests) | 100% |
| API Gateway | 9 | Gateway routing tests | 100% |
| **Total** | **18** | **20+** | **100%** |

### Testing Documentation

Comprehensive testing evidence is provided in the repository:

1. **API_TESTING_EVIDENCE.md**
   - Detailed test cases for all endpoints
   - Request/Response examples
   - Error handling verification
   - End-to-end workflow testing
   - Performance metrics

2. **Microservices_API_Tests.postman_collection.json**
   - Complete Postman collection
   - All API endpoints configured
   - Organized by service
   - Import-ready for verification

### Sample API Tests

#### Item Service
```bash
GET /items - List all items
POST /items - Add new item
GET /items/{id} - Get item by ID
Error handling validation
```

#### Order Service
```bash
GET /orders - List all orders
POST /orders - Place new order
GET /orders/{id} - Get order by ID
Input validation testing
```

#### Payment Service
```bash
GET /payments - List all payments
POST /payments/process - Process payment
GET /payments/{id} - Get payment by ID
Negative amount validation
```

#### End-to-End Workflow
```bash
Browse items → Place order → Process payment → Verify completion
```

---

## Project Deliverables Checklist

### Code & Repository
- [x] Complete source code for all microservices
- [x] Dockerfiles for each service
- [x] docker-compose.yml for orchestration
- [x] README.md with setup instructions
- [x] .gitignore files configured
- [x] Git submodules properly configured

### Docker Setup
- [x] Individual service Dockerfiles
- [x] Docker Compose configuration
- [x] Services successfully build
- [x] Services run in containers
- [x] Network configuration (microservices-net)
- [x] Port mappings configured

### API Testing Evidence
- [x] API_TESTING_EVIDENCE.md with detailed tests
- [x] Postman collection exported
- [x] All endpoints tested via Gateway
- [x] Direct service access tested
- [x] Error handling verified
- [x] End-to-end workflow documented
- [x] Success/failure scenarios covered

### Documentation
- [x] Comprehensive README.md
- [x] Architecture diagram in README
- [x] Setup and installation instructions
- [x] API endpoint documentation
- [x] Testing documentation
- [x] Docker setup guide

---

## How to Verify the Submission

### For Evaluators

1. **Clone the repository:**
   ```bash
   git clone --recursive https://github.com/CTSElab5/root_service.git
   cd root_service
   ```

2. **Build and run:**
   ```bash
   docker-compose build
   docker-compose up
   ```

3. **Verify services are running:**
   ```bash
   docker ps
   ```

4. **Test the APIs:**
   - Import `Microservices_API_Tests.postman_collection.json` into Postman
   - Run the collection to test all endpoints
   - Or use cURL commands from API_TESTING_EVIDENCE.md

5. **Access the services:**
   - API Gateway: http://localhost:8086
   - Item Service: http://localhost:8081
   - Order Service: http://localhost:8082
   - Payment Service: http://localhost:8083

---

## Key Features Implemented

### Microservices Architecture
- Service isolation and independence
- Container-based deployment
- API Gateway pattern
- Service discovery via Gateway routing
- Inter-service communication
- Network isolation with Docker bridge network

### API Implementation
- RESTful API design
- JSON request/response format
- Proper HTTP status codes
- Input validation
- Error handling
- CRUD operations

### DevOps Practices
- Dockerized all services
- Docker Compose orchestration
- Git version control with submodules
- Maven build automation
- Multi-stage Docker builds
- Environment separation

---

## Learning Outcomes

Through this project, we successfully:

1. Designed and implemented a complete microservices architecture
2. Containerized multiple Spring Boot applications using Docker
3. Configured API Gateway for request routing
4. Implemented RESTful APIs with proper error handling
5. Used Docker Compose for multi-container orchestration
6. Managed code across multiple repositories using Git submodules
7. Conducted comprehensive API testing with documentation
8. Followed best practices for microservices development

---

## Contact Information

**Team:** CTSElab5  
**GitHub Organization:** https://github.com/CTSElab5

For any questions or clarifications regarding this submission, please contact via GitHub issues in the main repository.

---

## Repository Contents Summary

### Files in Root Repository
```
microservice_ctse/
├── README.md                                    # Complete documentation
├── API_TESTING_EVIDENCE.md                      # Detailed test results
├── Microservices_API_Tests.postman_collection.json  # Postman tests
├── SUBMISSION.md                                # This document
├── docker-compose.yml                           # Docker orchestration
├── .gitmodules                                  # Git submodule config
├── gateway2/                                    # API Gateway service
├── item/                                        # Item microservice
├── order/                                       # Order microservice
└── payment2/                                    # Payment microservice
```

### Each Service Contains
- Source code (src/main/java)
- Application configuration (application.properties/yml)
- Maven configuration (pom.xml)
- Dockerfile
- Unit tests
- Maven build artifacts

---

## Conclusion

This submission contains a fully functional microservices system with complete Docker setup and comprehensive API testing evidence. All requirements have been met and documented.

**Repository Link:** https://github.com/CTSElab5/root_service.git

---


