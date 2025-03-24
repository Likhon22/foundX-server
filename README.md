# **FoundX - Lost and Found Management System**

![FoundX Logo](https://cdn.pixabay.com/photo/2015/10/05/22/37/blank-profile-picture-973460_960_720.png)

## 📑 **Table of Contents**

- [Overview](#overview)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [API Documentation](#api-documentation)
- [Installation Guide](#installation-guide)
- [Environment Variables](#environment-variables)
- [Database Setup](#database-setup)
- [Running the Application](#running-the-application)
- [Project Structure](#project-structure)
- [Deployment](#deployment)
- [Contributors](#contributors)

## 🌟 **Overview**

FoundX is a comprehensive lost and found management system designed to help users report found items and allow others to claim them through a verification process. The platform facilitates the reconnection of lost items with their rightful owners through a structured, secure, and user-friendly interface.

## 🚀 **Features**

- **User Management**

  - User registration and authentication
  - Profile management
  - Role-based access control (Admin/User)

- **Item Management**

  - Report found items with details and images
  - Categorize items for better organization
  - Search and filter capabilities
  - Location-based item discovery

- **Claim Process**

  - Submit claim requests for lost items
  - Answer verification questions
  - Receive notifications on claim status
  - Approve or reject claims with feedback

- **Admin Features**
  - User management
  - Category management
  - Monitor platform activities

## 💻 **Technology Stack**

### Backend

- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **TypeScript** - Type-safe JavaScript
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB object modeling

### Authentication & Security

- **JWT** - Token-based authentication
- **Bcrypt.js** - Password hashing

### File Storage

- **Cloudinary** - Cloud-based image management
- **Multer** - File upload handling

### Email Service

- **Nodemailer** - Email sending functionality

### Validation

- **Zod** - Schema validation

### Development Tools

- **ESLint** - Code linting
- **Prettier** - Code formatting
- **ts-node-dev** - TypeScript development server

## 📝 **API Documentation**

### Authentication Endpoints

- `POST /api/v1/auth/register` - Register a new user
- `POST /api/v1/auth/login` - Log in a user
- `POST /api/v1/auth/change-password` - Change user password
- `POST /api/v1/auth/refresh-token` - Refresh authentication token

### User Endpoints

- `POST /api/v1/users/create-user` - Create a new user (Admin only)
- `GET /api/v1/users` - Get all users
- `GET /api/v1/users/:id` - Get user by ID

### Profile Endpoints

- `GET /api/v1/profile` - Get user profile
- `PATCH /api/v1/profile` - Update user profile

### Item Category Endpoints

- `POST /api/v1/item-categories` - Create item category (Admin only)
- `GET /api/v1/item-categories` - Get all item categories
- `GET /api/v1/item-categories/:id` - Get category by ID
- `PUT /api/v1/item-categories/:id` - Update category (Admin only)
- `DELETE /api/v1/item-categories/:id` - Delete category (Admin only)

### Item Endpoints

- `POST /api/v1/items` - Create a new item
- `GET /api/v1/items` - Get all items
- `GET /api/v1/items/:id` - Get item by ID
- `PUT /api/v1/items/:id` - Update item
- `DELETE /api/v1/items/:id` - Delete item

### Claim Request Endpoints

- `POST /api/v1/claim-request` - Create claim request
- `GET /api/v1/claim-request/received-claim-request` - Get received claim requests
- `GET /api/v1/claim-request/my-claim-request` - Get user's claim requests
- `GET /api/v1/claim-request/:id` - Get claim request by ID
- `PUT /api/v1/claim-request/:id` - Update claim request status with feedback

### Search Endpoints

- `GET /api/v1/search-items` - Search items

## ⚙️ **Installation Guide**

### Prerequisites

- Node.js (v14.x or later)
- MongoDB Atlas account
- Cloudinary account
- Gmail account

### Step 1: Clone the Repository

```bash
git clone https://github.com/yourusername/foundx-server.git
cd foundx-server
```

### Step 2: Install Dependencies

```bash
# Using npm
npm install

# Using yarn
yarn install
```

## 🔐 **Environment Variables**

Create a `.env` file in the project root directory with the following variables:

```bash
# Environment
NODE_ENV=development

# Port
PORT=5000

# Database URL
DB_URL=mongodb+srv://<username>:<password>@cluster0.xxxxx.mongodb.net/<dbname>?retryWrites=true&w=majority

# Bcrypt Salt Rounds
BCRYPT_SALT_ROUNDS=12

# JWT Secrets and Expiry
JWT_ACCESS_SECRET=your_access_secret_key
JWT_ACCESS_EXPIRES_IN=7d
JWT_REFRESH_SECRET=your_refresh_secret_key
JWT_REFRESH_EXPIRES_IN=1y

# Admin Credentials
ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=secure_password
ADMIN_PROFILE_PHOTO=https://example.com/profile-photo.png
ADMIN_MOBILE_NUMBER=1234567890

# Cloudinary Credentials
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Email Configuration
SENDER_EMAIL=your_email@gmail.com
SENDER_APP_PASS=your_app_password
```

## 🗄️ **Database Setup**

### MongoDB Atlas Setup

1. **Create a MongoDB Atlas Account**:

   - Visit [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) and sign up or log in

2. **Create a Cluster**:

   - Click "Build a Cluster" and follow the instructions
   - Choose the free tier option for development

3. **Database Access**:

   - Create a new database user with password authentication
   - Set appropriate read/write permissions

4. **Network Access**:

   - Add your IP address to the IP Access List
   - For development, you can allow access from anywhere (0.0.0.0/0)

5. **Connect to Your Application**:
   - Click "Connect" > "Connect your application"
   - Select Node.js and copy the connection string
   - Replace `<username>`, `<password>`, and `<dbname>` with your credentials

## 📧 **Email Configuration**

### Gmail App Password Setup

1. **Enable 2-Step Verification**:

   - Go to your [Google Account Security](https://myaccount.google.com/security)
   - Enable 2-Step Verification

2. **Create App Password**:

   - Go to [App passwords](https://myaccount.google.com/apppasswords)
   - Select "Mail" as the app and your device type
   - Click "Generate" and copy the 16-character password

3. **Add to Environment Variables**:
   - Set `SENDER_EMAIL` to your Gmail address
   - Set `SENDER_APP_PASS` to the generated app password

## ☁️ **Cloudinary Setup**

1. **Create a Cloudinary Account**:

   - Visit [Cloudinary](https://cloudinary.com/) and sign up

2. **Get API Credentials**:
   - From your dashboard, note your Cloud name, API Key, and API Secret
   - Add these to your environment variables

## 🏃‍♂️ **Running the Application**

### Development Mode

```bash
# Using npm
npm run dev

# Using yarn
yarn dev
```

### Production Mode

```bash
# Build the project
npm run build
# or
yarn build

# Start the server
npm start
# or
yarn start
```

The server will be running at `http://localhost:5000` (or the port defined in your environment variables).

## 📂 **Project Structure**

```
foundx-server/
├── src/
│   ├── app/
│   │   ├── builder/          # Query builder utilities
│   │   ├── config/           # Configuration files
│   │   ├── errors/           # Error handling utilities
│   │   ├── interfaces/       # TypeScript interfaces
│   │   ├── middlewares/      # Express middlewares
│   │   ├── modules/          # Feature modules
│   │   │   ├── Auth/         # Authentication module
│   │   │   ├── ClaimRequest/ # Claim request module
│   │   │   ├── Item/         # Item module
│   │   │   ├── ItemCategory/ # Item category module
│   │   │   ├── Meilisearch/  # Search module
│   │   │   ├── Profile/      # User profile module
│   │   │   └── User/         # User module
│   │   ├── routes/           # API routes
│   │   ├── utils/            # Utility functions
│   │   └── zod/              # Zod validations
│   ├── views/                # Email templates
│   ├── app.ts                # Express app setup
│   └── server.ts             # Server entry point
├── .env                      # Environment variables
├── .eslintrc.json           # ESLint configuration
├── .gitignore               # Git ignore file
├── .prettierrc              # Prettier configuration
├── package.json             # Project dependencies
├── tsconfig.json            # TypeScript configuration
└── README.md                # Project documentation
```

## 🚢 **Deployment**

### Vercel Deployment

The project includes a `vercel.json` configuration file for easy deployment to Vercel:

1. **Install Vercel CLI**:

   ```bash
   npm install -g vercel
   ```

2. **Deploy to Vercel**:

   ```bash
   vercel
   ```

3. **Environment Variables**:
   - Add all the required environment variables in the Vercel dashboard

### Other Deployment Options

- **Heroku**: Use the Heroku CLI to deploy
- **AWS**: Deploy to AWS EC2 or Elastic Beanstalk
- **Digital Ocean**: Deploy as a Digital Ocean App or Droplet
