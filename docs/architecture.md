# Architecture

The architecture of the project is based on the following components:

- **Frontend**: The frontend is a web application that is built using React. It is responsible for rendering the user interface and handling user interactions. The frontend communicates with the backend via RESTful APIs.
- **API Gateway**: The API Gateway is responsible for routing requests from the frontend to the appropriate microservices. It is implemented using Django.
- **Microservices**: The microservices are responsible for handling specific business logic. Each microservice is implemented as a separate Django application and communicates with other microservices via RESTful APIs. Each microservice has its own database.

The architecture follows a microservices pattern, where each microservice is responsible for a specific set of features. This allows for better scalability, maintainability, and flexibility in the application.
