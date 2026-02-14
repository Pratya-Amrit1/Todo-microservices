🚀 Todo Microservices

A scalable Microservices-based Todo Application built with Node.js, MongoDB, and RabbitMQ, implementing event-driven architecture.

🔹 Flow

User is created via User Service

Task is created via Task Service

Task event is published to RabbitMQ

Notification Service consumes event

Notification is triggered (currently logged)

🛠 Tech Stack
Layer	Technology
⚙ Runtime	Node.js
💻 Language	JavaScript (ES Modules)
🚀 Framework	Express.js
🗄 Database	MongoDB
🐇 Message Broker	RabbitMQ
🔐 Security	bcrypt (password hashing), JWT
🌐 Middleware	cors
🔧 Config	dotenv
📦 Queue Client	amqplib
🐳 Containerization	Docker (for RabbitMQ)
📁 Project Structure
Todo-microservices/
├── user-service/
├── task-service/
├── notification-service/
└── README.md


Each service follows a clean architecture pattern:

src/
 ├── controllers/
 ├── models/
 ├── routes/
 ├── db/
 ├── utils/
 ├── app.js
 └── index.js


✔ Clean separation of concerns
✔ Independent service logic
✔ Scalable folder structure

📊 Data Models
👤 User Model

name (String, required)

email (String, unique, required)

password (Hashed using bcrypt)

timestamps (createdAt, updatedAt)

📝 Task Model

title (String, required)

description (String, required)

status (pending | in-progress | completed)

userId (Reference to user)

timestamps

🌐 Services & APIs
👤 User Service (Port 3000)
Method	Endpoint	Description
POST	/api/v1/users/register	Register a user
GET	/api/v1/users/getUsers	Get all users
📝 Task Service (Port 3001)
Method	Endpoint	Description
GET	/api/v1/tasks	Service check
POST	/api/v1/tasks/create	Create task
GET	/api/v1/tasks/getTasks?userId=<id>	Get user tasks

✔ Saves task to MongoDB
✔ Publishes task event to RabbitMQ

🔔 Notification Service

Consumes messages from todo queue

Processes task events

Logs notifications (extendable to email/SMS/push)

🔄 Message Flow (Event Driven)
Client → Task Service → MongoDB
                   ↓
                RabbitMQ (Queue: todo)
                   ↓
          Notification Service


✨ Fully asynchronous communication
✨ Loose coupling between services
✨ Production-style microservices pattern

⚙ Prerequisites

Node.js (v14+)

MongoDB (Local or Atlas)

RabbitMQ (Docker recommended)

🐳 Run RabbitMQ using Docker
docker run -d --hostname rabbit \
--name rabbitmq \
-p 5672:5672 -p 15672:15672 \
rabbitmq:3-management


Access dashboard:

http://localhost:15672
Username: guest
Password: guest

🚀 Setup & Run
Install dependencies
cd user-service && npm install
cd ../task-service && npm install
cd ../notification-service && npm install

Start Services (3 Terminals)
# User Service
cd user-service && npm start

# Task Service
cd task-service && npm start

# Notification Service
cd notification-service && npm start

🔐 Environment Variables
User Service (user-service/.env)
PORT=3000
MONGO_URI=your_mongodb_uri

Task Service (task-service/.env)
PORT=3001
MONGO_URI=your_mongodb_uri
RABBITMQ_URL=amqp://guest:guest@localhost:5672

Notification Service (notification-service/.env)
RABBITMQ_URL=amqp://guest:guest@localhost:5672

🧪 Testing the Flow

Register a user

Create a task

Check RabbitMQ dashboard

Observe notification service logs

✔ End-to-end microservices flow working

🔮 Future Improvements

Add API Gateway

Add JWT-based authentication across services

Add Docker Compose for full containerization

Add Kubernetes deployment

Add Email/SMS notification integration

Add centralized logging & monitoring

📌 Key Concepts Implemented

Microservices Architecture

Event-Driven Architecture

Asynchronous Messaging

Producer–Consumer Pattern

Service Decoupling

Docker-based Infrastructure

👨‍💻 Author

Pratya Amrit
Developer | Coder

Built as part of a continuous learning series on Microservices Architecture 🚀
