# EGRents - Property Rental Platform

A comprehensive full-stack property rental platform built with modern web technologies, enabling seamless property management and rental experiences for both tenants and property managers.

##  Features

### For Tenants
- Browse available properties with interactive map visualization
- Advanced search and filtering capabilities
- Location-based property discovery using Mapbox
- Apply for properties with streamlined application process
- User dashboard for managing applications and favorites

### For Property Managers
- List and manage properties with detailed information
- View and process tenant applications
- Approve/reject applications with workflow management
- Analytics dashboard for property performance
- Bulk property management tools

### General Features
- Secure user authentication with role-based access
- Responsive design for mobile and desktop
- Interactive maps with geospatial filtering
- Advanced search with multiple parameters

## 🛠️ Tech Stack

### Frontend
- **React 19** - Modern UI library
- **Next.js 15** - Full-stack React framework with SSR
- **TypeScript** - Type-safe JavaScript
- **Tailwind CSS** - Utility-first CSS framework
- **Mapbox GL JS** - Interactive maps and location services

### Backend
- **Node.js** - JavaScript runtime
- **Express.js** - Web application framework
- **TypeScript** - Type-safe server-side code
- **RESTful APIs** - Standardized API architecture

### Cloud Infrastructure (AWS)
- **AWS Amplify** - Frontend hosting and CI/CD
- **Amazon Cognito** - User authentication and authorization
- **Amazon RDS** - Relational database service
- **Amazon S3** - Object storage for images and files
- **Amazon EC2** - Scalable compute capacity
- **API Gateway** - API management and routing
- **VPC** - Secure network infrastructure

### Database
- **PostgreSQL** - Primary relational database
- **Prisma ORM** - Database toolkit and ORM

## 🏗️ Architecture

The application follows a modern cloud-native architecture:

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Frontend      │    │   API Gateway    │    │   Backend       │
│   (Amplify)     │◄──►│                  │◄──►│   (EC2)         │
│                 │    │                  │    │                 │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                                │                        │
                       ┌────────▼────────┐              │
                       │   Cognito       │              │
                       │   (Auth)        │              │
                       └─────────────────┘              │
                                                         │
                       ┌─────────────────┐    ┌─────────▼─────────┐
                       │   S3 Bucket     │    │   RDS (PostgreSQL)│
                       │   (Storage)     │    │   (Database)      │
                       └─────────────────┘    └───────────────────┘
```

## 🚦 Getting Started

### Prerequisites
- Node.js 22+
- npm or yarn
- AWS CLI configured
- PostgreSQL database

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/priyanshu496/EGRents.git
   cd EGRents
   ```

2. **Install dependencies**
   ```bash
   # Frontend
   cd frontend
   npm install

   # Backend
   cd ../backend
   npm install
   ```

3. **Environment Setup**
   
   Create `.env.local` in frontend directory:
   ```env
   NEXT_PUBLIC_MAPBOX_TOKEN=your_mapbox_token
   NEXT_PUBLIC_API_BASE_URL=your_backend_url
   NEXT_PUBLIC_USER_POOL_ID=your_cognito_user_pool_id
   NEXT_PUBLIC_USER_POOL_CLIENT_ID=your_cognito_client_id
   ```

   Create `.env` in backend directory:
   ```env
   PORT=your_port || 80
   DATABASE_URL=your_postgresql_connection_string
   S3_BUCKET_NAME=your_s3_bucket_name
   ```

4. **Database Setup**
   ```bash
   cd backend
   npm run prisma:generate
   npx prisma migrate dev --name init
   npm run seed
   ```

5. **Run Development Servers**
   ```bash
   # Frontend
   cd frontend
   npm run dev

   # Backend (in another terminal)
   cd backend
   npm run dev
   ```

## 📱 Usage

1. **Sign Up/Login**: Create an account as either a Tenant or Property Manager
2. **For Tenants**: Browse properties, use map features, apply for rentals
3. **For Managers**: List properties, manage applications, view analytics
4. **Interactive Maps**: Use location-based filtering and search

## 🔐 Authentication Flow

The application uses AWS Cognito for secure authentication:
- User registration with email verification
- Role-based access control (Tenant/Manager)
- Secure password policies

## 📊 Database Schema

Key entities include:
- **Users** (Tenants, Managers)
- **Properties** (Listings with geospatial data)
- **Applications** (Rental applications with status tracking)
- **Locations** (Geographic data for properties)
- **Payments** (Transaction records)

## 🌐 API Endpoints

### Properties
- `GET /api/properties` - List all properties with filters
- `POST /api/properties` - Create new property (Manager only)
- `GET /api/properties/:id` - Get property details
- `PUT /api/properties/:id` - Update property (Manager only)

### Applications
- `POST /api/applications` - Submit rental application
- `GET /api/applications` - Get user applications
- `PUT /api/applications/:id` - Update application status (Manager only)

### Users
- `GET /api/users/profile` - Get user profile
- `PUT /api/users/profile` - Update user profile

## 🚀 Deployment

The application is deployed using AWS services:

1. **Frontend**: Deployed on AWS Amplify with automatic CI/CD
2. **Backend**: Deployed on EC2 with load balancing
3. **Database**: Amazon RDS for PostgreSQL
4. **Storage**: S3 for property images and documents

## 📈 Performance Optimizations

- Server-side rendering with Next.js
- Image optimization with Next.js Image component
- Database query optimization with indexed fields
- Caching strategies for frequently accessed data
- CDN integration for static assets

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request


Project Link: [https://github.com/priyanshu496/EGRents](https://github.com/priyanshu496/EGRents)

## 🙏 Acknowledgments

- [Next.js](https://nextjs.org/) for the amazing React framework
- [AWS](https://aws.amazon.com/) for robust cloud infrastructure
- [Mapbox](https://mapbox.com/) for interactive mapping capabilities
- [Tailwind CSS](https://tailwindcss.com/) for utility-first styling
