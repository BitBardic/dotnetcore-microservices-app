# dotnetcore-microservices-app

![dotnet-microservices-architecture](https://user-images.githubusercontent.com/22410650/95888476-091c8500-0d79-11eb-90e4-e38d853522b9.png)

There is a couple of microservices which implemented **e-commerce** modules over **Product, Basket** and **Ordering** microservices with **NoSQL (MongoDB, Redis)** and **Relational databases (Sql Server)** with communicating over **RabbitMQ Event Driven Communication** and using **Ocelot API Gateway**.

## Whats Including In This Repository
We have implemented below **features over the dotnetcore-microservices-app repository**.

#### Catalog microservice which includes; 
* ASP.NET Core Web API application 
* REST API principles, CRUD operations 
* **Mongo DB NoSQL database** connection on docker
* N-Layer implementation with Repository Pattern
* Swagger Open API implementation
* Dockerfile implementation

#### Basket microservice which includes;
* ASP.NET Core Web API application 
* REST API principles, CRUD operations 
* **Redis** connection as a Database on docker
* Redis connection implementation
* **RabbitMQ trigger event queue** when checkout cart
* Swagger Open API implementation
* Dockerfile implementation

#### RabbitMQ messaging library which includes;
* Base **EventBus implementation** and add references Microservices

#### Ordering microservice which includes; (over the catalog specs)
* ASP.NET Core Web API application 
* **Entity Framework Core on SQL Server** docker
* REST API principles, CRUD operations 
* **Consuming RabbitMQ** messages
* **Clean Architecture** implementation with CQRS Design Pattern
* Event Sourcing
* Implementation of MediatR, Autofac, FluentValidator, AutoMapper
* Swagger Open API implementation
* Dockerfile implementation

#### API Gateway Ocelot microservice which includes;
* **Routing** to inside microservices
* Dockerization api-gateway

#### WebUI ShoppingApp microservice which includes;
* Asp.net Core Web Application with Razor template
* Call **Ocelot APIs** with **HttpClientFactory**
* Aspnet core razor tools - View Components, partial Views, Tag Helpers, Model Bindings and Validations, Razor Sections etc.. 

#### Docker Compose establishment with all microservices on docker;
* Dockerization of microservices
* **Dockerization** of database
* Override Environment variables

## Run The Project
You will need the following tools:

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)
* [.Net Core 3.1 or later](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [Docker Desktop](https://www.docker.com/products/docker-desktop)

### Installing
Follow these steps to get your development environment set up: (Before Run Start the Docker Desktop)
1. Clone the repository
2. At the root directory which include **docker-compose.yml** files, run below command:
```csharp
docker-compose -f docker-compose.yml -f docker-compose.override.yml up –d
```
3. Wait for docker compose all microservices. That’s it! (some microservices need extra time to work so please wait if not worked in first shut)

4. You can **launch microservices** as below urls:
* **RabbitMQ -> http://localhost:15672/**
* **Catalog API -> http://localhost:8000/swagger/index.html**
* **Basket API -> http://localhost:8001/swagger/index.html**
* **Order API -> http://localhost:8002/swagger/index.html**
* **API Gateway -> http://localhost:7000/Order?username=swn**
* **Web UI -> http://localhost:8003/**

5. Launch http://localhost:8003/ in your browser to view the Web UI. You can use Web project in order to **call microservices over API Gateway**. When you **checkout the basket** you can follow **queue record on RabbitMQ dashboard**.

