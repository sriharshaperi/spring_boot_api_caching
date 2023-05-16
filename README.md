# Spring Boot API Caching

This project is a Spring Boot-based REST API that provides support for handling structured data in JSON format. It offers CRUD operations with merge support, cascaded delete, and validation capabilities. The API is designed to store data in a key/value store, utilize advanced semantics for operations like update if not changed, leverage Elastic for search with join, enable parent-child indexing, and provide queueing functionality. Additionally, the API incorporates security measures to protect the data and ensure authorized access.

## Features

**Structured Data Handling:** The API supports handling any structured data in JSON format, allowing flexibility in the data model.

**CRUD Operations:** The API provides endpoints for Create, Read, Update, and Delete operations on the data. It includes merge support, allowing updates to specific fields without overwriting the entire object.

**Validation:** The API enforces validation rules to ensure the integrity and consistency of the data. Invalid requests will be rejected with appropriate error responses.

**JSON Schema:** A JSON Schema is provided that describes the data model used by the API. It serves as a reference for the structure and constraints of the JSON data.

**Advanced Semantics:** The API offers advanced semantics for specific operations. For example, it provides an "update if not changed" functionality, allowing clients to update an object only if it has not been modified since retrieval.

**Key/Value Store:** The data is stored in a key/value store, providing efficient and scalable storage for the API's data.

**Search with Join using Elastic:** The API integrates with Elasticsearch to enable powerful search capabilities, including join operations to retrieve related data efficiently.

**Parent-Child Indexing:** The API supports parent-child indexing, allowing the modeling of relationships between entities and efficient querying based on those relationships.

**Queueing:** Queueing functionality is implemented to handle asynchronous operations or perform background tasks efficiently. This ensures responsiveness and scalability of the API.

**Security:** The API includes security measures to protect the data and control access. It provides authentication and authorization mechanisms to ensure that only authorized users can interact with the API.

## Getting Started

To run the Spring Boot REST API locally, follow these steps:

## Clone the repository:

git clone https://github.com/sriharshaperi/spring_boot_api_caching.git

## Install the required dependencies

Following dependencies are required to run this project:

1. JDK 17
2. redis-server v7.0.5
3. redis-cli (optional)
4. RabbitMQ 3.11.10
5. Elasticsearch v7.14
6. Kibana v7.14

Configure the key/value store and Elasticsearch connection settings in the application configuration file.

Build and run the application using your preferred build tool (Maven or Gradle).

# Using Maven

mvn spring-boot:run

# Using Gradle

gradle bootRun

The API will be accessible at http://localhost:8080. Refer to the API documentation or JSON Schema for the available endpoints and data model.

## API documentation

### API Endpoints

localhost : http://localhost:8080

1. GET /token
2. POST /validate
3. POST /plan
4. GET /{objectType}/{objectId}
5. DELETE /{objectType}/{objectId}
6. PUT /plan/{objectId}
7. PATCH /{objectType}/{objectId}

### JSON Request Payload

Use this payload for POST, PUT and PATCH requests

{
"planCostShares": {
"deductible": 2000,
"\_org": "example.com",
"copay": 23,
"objectId": "1234vxc2324sdf-501",
"objectType": "membercostshare"
},
"linkedPlanServices": [
{
"linkedService": {
"_org": "example.com",
"objectId": "1234520xvc30asdf-502",
"objectType": "service",
"name": "Yearly physical"
},
"planserviceCostShares": {
"deductible": 10,
"_org": "example.com",
"copay": 0,
"objectId": "1234512xvc1314asdfs-503",
"objectType": "membercostshare"
},
"_org": "example.com",
"objectId": "27283xvx9asdff-504",
"objectType": "planservice"
},
{
"linkedService": {
"_org": "example.com",
"objectId": "1234520xvc30sfs-505",
"objectType": "service",
"name": "well baby"
},
"planserviceCostShares": {
"deductible": 10,
"_org": "example.com",
"copay": 175,
"objectId": "1234512xvc1314sdfsd-506",
"objectType": "membercostshare"
},
"_org": "example.com",
"objectId": "27283xvx9sdf-507",
"objectType": "planservice"
}
],
"\_org": "example.com",
"objectId": "12xvxc345ssdsds-508",
"objectType": "plan",
"planType": "inNetwork",
"creationDate": "12-12-2017"
}

## Security Considerations

The Spring Boot REST API incorporates security measures to protect the data and control access. It includes authentication and authorization mechanisms that can be customized based on your specific requirements. RS256(OAuth2.0) and ED512(JWT Auth Token) security algorthims have been used.
