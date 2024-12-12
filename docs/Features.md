# Features of Microservice Template

Microservices architecture is a popular design pattern that promotes the development of independent, modular services. This approach can enhance system resilience by isolating potential failure points, making it more robust against unexpected faults. This template is built based on Django Web Framework.

## 1. Services

This template is designed to be generic and adaptable to any type of application. Below is a list of services included in this template, but you can add more services as needed based on these examples.

1. **Authentication Service** - used to authenticate and authorize users.
2. **Main Service** - main service which can contain mainn features of the application.
3. **API Gateway** - helps to redirect requests to the services.
4. **Analytics Service** - used to collect user actions data to future improvements of services.

### 1.1. Authentication Service

**Purpose**: This service is responsible for authenticating and authorizing users. It provides endpoints for user registration, login, and logout. It also generates and validates JWT tokens for authenticated users.

**Key Features**:

- User registration
- User login and logout with JWT token.
- Profile management (Profile picture, username, email, etc.)
- Role-based access control (RBAC) and permissions
- Password reset and change

**Database**: This service can have its own database to store user information, or it can integrate with an external identity provider (e.g., LDAP, OAuth, etc.). This service uses PostgreSQL as a database. (You can change it to any other database as per your requirement)

**Sample Endpoints**:

- `/accounts/v1/register` - POST request to register a new user.
- `/accounts/v1/login` - POST request to login and get JWT token.
- `/accounts/v1/logout` - POST request to logout and invalidate JWT token.
- `/accounts/v1/refresh` - POST request to refresh JWT token.
- `/accounts/v1/user` - GET request to get user information.
- `/accounts/v1/change-password` - POST request to change user password.
- `/accounts/v1/reset-password` - POST request to reset user password.

### 1.2. Main Service

**Purpose**: This service is the main service of the application. It can contain the main features of the application, such as CRUD operations, business logic, and data processing.

**Key Features**:

- CRUD operations for content (e.g., create/update blog posts, products, etc.).
- Pagination and filtering.
- Category or tag management for organizing resources.

**Database**: This service can have its own database to store application-specific data. This service uses PostgreSQL or MongoDB as a database. (You can change it to any other database as per your requirement)

**Example use case**: A blog application can use this service to manage blog posts, categories, and tags.

**Sample Endpoints**:

- `/main/v1/posts` - GET request to list all posts.
- `/main/v1/posts/{id}` - GET request to get a specific post.
- `/main/v1/posts` - POST request to create a new post.
- `/main/v1/posts/{id}` - PUT request to update a post.

### 1.3. API Gateway

**Purpose**: This service acts as an entry point for all incoming requests and routes them to the appropriate microservice based on the request path. It helps to decouple the client from the individual services and provides a unified interface for the client to interact with the microservices.

**Key Features**:

- Request routing and load balancing.
- Authentication and authorization.
- Rate limiting and throttling.
- Logging and monitoring.

**Sample Endpoints**:

- `accounts/*` - Routes requests to the Authentication Service.
- `main/*` - Routes requests to the Main Service.

### 1.4. Analytics Service

**Purpose**: This service collects user actions data to analyze user behavior, improve services, and make data-driven decisions. It can track user interactions, events, and metrics to provide insights into user engagement and system performance.

**Key Features**:

- Event tracking and logging.
- User behavior analysis.
- Performance monitoring.
- Data visualization and reporting.
- Integration with third-party analytics tools.

**Database**: This service can have its own database. As it tracks user activity and system performance, it is using time-series databases like InfluxDB to store metrics data. (You can change it to any other database as per your requirement)

**Sample Endpoints**:

- `/analytics/v1/track-event` - POST request to track user events.
- `/analytics/v1/user-activity` - GET request to get user activity data.
- `/analytics/v1/performance` - GET request to get system performance metrics.
- `/analytics/v1/reports` - GET request to generate analytics reports.

## 2. Infrastructure

This template provides a set of infrastructure components to support the microservices architecture. It includes the following components:

1. **Docker Compose** - to define and run multi-container Docker applications. It simplifies the process of building, running, and managing containers. You can define the services, networks, and volumes in a single YAML file.
2. **NGINX** - to act as a reverse proxy server and handle incoming requests. It can route requests to the appropriate microservice based on the request path. NGINX can also handle SSL termination, load balancing, and caching.
3. **PostgreSQL** - as a relational database to store application data. It provides data persistence and supports SQL queries for data manipulation. You can define the database schema, tables, and relationships using SQL scripts.
4. **InfluxDB** - as a time-series database to store metrics data. It is optimized for storing and querying time-series data, such as user activity logs, system performance metrics, and sensor data. You can define retention policies and continuous queries to manage data retention and aggregation.
