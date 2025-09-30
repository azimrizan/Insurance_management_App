# Insurance Management System

A comprehensive insurance management system built with Node.js/Express backend and Angular frontend, featuring GraphQL API, JWT authentication, and role-based access control.

## 🏗️ Architecture

- **Backend**: Node.js, Express, GraphQL (Apollo Server), MongoDB (Mongoose)
- **Frontend**: Angular 20, TypeScript, Tailwind CSS
- **Authentication**: JWT tokens with role-based access control
- **Database**: MongoDB with Mongoose ODM

## 🚀 Quick Start

### Prerequisites

- Node.js (v18 or higher)
- MongoDB (local or cloud instance)
- npm or yarn

### 1. Clone and Setup

```bash
git clone <your-repo-url>
cd Insurance_Management
```

### 2. Backend Setup

```bash
cd backend
npm install
```

Create a `.env` file in the backend directory:
```env
MONGO_URI=mongodb://localhost:27017/insurance_management
JWT_SECRET=your_super_secure_jwt_secret_key_here_change_in_production
JWT_EXPIRES_IN=7d
PORT=5000
NODE_ENV=development
```

### 3. Frontend Setup

```bash
cd ../frontend
npm install
```

### 4. Start MongoDB

Make sure MongoDB is running on your system:
```bash
# Windows (if installed as service)
net start MongoDB

# macOS (with Homebrew)
brew services start mongodb-community

# Linux
sudo systemctl start mongod
```

### 5. Run the Application

**Terminal 1 - Backend:**
```bash
cd backend
npm run dev
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm start
```

The application will be available at:
- Frontend: http://localhost:4200
- Backend API: http://localhost:5000
- GraphQL Playground: http://localhost:5000/graphql

## 🔧 PowerShell Execution Policy Fix

If you encounter PowerShell execution policy errors on Windows:

```powershell
# Run as Administrator
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Or use Command Prompt instead:
```cmd
cd backend
npm run dev
```

## 📊 Features

### User Management
- User registration and authentication
- Role-based access (Customer, Agent, Admin)
- JWT token-based security

### Policy Management
- Create, read, update, delete insurance policies
- Policy types and coverage management
- Customer-policy relationships

### Claims Processing
- Submit and track insurance claims
- Status management (submitted, under_review, approved, rejected)
- Agent and admin claim processing

### Payment Management
- Payment tracking and status updates
- Multiple payment methods support
- Due date and payment history

### Admin Dashboard
- System overview and analytics
- User management
- Policy and claim oversight

## 🛠️ API Endpoints

### REST API
- `POST /api/v1/auth/register` - User registration
- `POST /api/v1/auth/login` - User login
- `GET /api/v1/auth/me` - Get current user

### GraphQL API
Access the GraphQL playground at `http://localhost:5000/graphql`

**Queries:**
- `me` - Get current user
- `policies` - Get user policies
- `claims` - Get user claims
- `payments` - Get user payments

**Mutations:**
- `signup` - User registration
- `login` - User login
- `createPolicy` - Create new policy
- `createClaim` - Submit new claim
- `updatePaymentStatus` - Update payment status

## 🔐 Authentication

The system uses JWT tokens for authentication. Include the token in requests:

```javascript
// REST API
headers: {
  'Authorization': 'Bearer <your-jwt-token>'
}

// GraphQL
headers: {
  'Authorization': 'Bearer <your-jwt-token>'
}
```

## 👥 User Roles

- **Customer**: Can view their own policies, claims, and payments
- **Agent**: Can manage policies and process claims for customers
- **Admin**: Full system access and user management

## 🗄️ Database Schema

### Users
- name, email, passwordHash, role, timestamps

### Policies
- policyNumber, type, premium, coverage, status, startDate, endDate, customer

### Claims
- claimNumber, policy, amount, status, description, submittedDate, processedDate

### Payments
- policy, amount, dueDate, paidDate, status, paymentMethod, reference

## 🚨 Troubleshooting

### Common Issues

1. **MongoDB Connection Error**
   - Ensure MongoDB is running
   - Check MONGO_URI in .env file
   - Verify database permissions

2. **JWT Token Errors**
   - Check JWT_SECRET in .env file
   - Ensure token is not expired
   - Verify token format in requests

3. **CORS Issues**
   - Backend CORS is configured for localhost:4200
   - Update CORS_ORIGIN in .env for production

4. **PowerShell Execution Policy**
   - Use Command Prompt instead of PowerShell
   - Or change execution policy as shown above

### Development Tips

- Use GraphQL playground for API testing
- Check browser console for frontend errors
- Monitor backend console for server logs
- Use MongoDB Compass for database inspection

## 📝 Environment Variables

### Backend (.env)
```env
MONGO_URI=mongodb://localhost:27017/insurance_management
JWT_SECRET=your_super_secure_jwt_secret_key_here_change_in_production
JWT_EXPIRES_IN=7d
PORT=5000
NODE_ENV=development
CORS_ORIGIN=http://localhost:4200
```

### Frontend (src/environments/)
```typescript
export const environment = {
  production: false,
  apiUrl: 'http://localhost:5000/api/v1',
  graphqlUrl: 'http://localhost:5000/graphql'
};
```

## 🎯 Next Steps

1. Set up MongoDB Atlas for production
2. Implement email notifications
3. Add file upload for claim documents
4. Implement payment gateway integration
5. Add comprehensive testing suite
6. Set up CI/CD pipeline

## 📞 Support

If you encounter any issues:
1. Check the troubleshooting section above
2. Verify all environment variables are set
3. Ensure MongoDB is running and accessible
4. Check console logs for specific error messages

---

**Happy Coding! 🚀**






