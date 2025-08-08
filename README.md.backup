# 💳 DueDesk - Payment Management System

A comprehensive debt and payment management application built with Node.js, React, and SQLite.

## 🚀 Features

- **Customer Management**: Add, edit, and track customer information
- **Payment Processing**: Handle cash, card, and UPI payments
- **Real-time Dashboard**: View payment statistics and customer status
- **Transaction History**: Complete audit trail of all transactions
- **Secure Authentication**: JWT-based admin authentication with bcrypt password hashing
- **Payment Cycles**: Track multiple payment cycles per customer
- **Responsive Design**: Works on desktop and mobile devices

## 🛠️ Tech Stack

**Backend:**
- Node.js with Express
- SQLite database
- JWT authentication
- bcrypt password hashing
- CORS enabled

**Frontend:**
- React with TypeScript
- Modern responsive UI
- Real-time data updates
- Payment processing interface

## 📦 Project Structure

```
duedesk/
├── duedesk-backend/          # Node.js API server
│   ├── index.js             # Main server file
│   ├── customers.db         # SQLite database
│   └── package.json
├── duedesk-dashboard/        # React frontend
│   ├── src/
│   │   ├── App.tsx          # Main React component
│   │   ├── Login.tsx        # Authentication component
│   │   └── ...
│   └── package.json
├── .env.example             # Environment variables template
└── render.yaml             # Render deployment config
```

## 🔧 Installation & Setup

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/AdityaJoshi-14/duedesk.git
   cd duedesk
   ```

2. **Backend Setup**
   ```bash
   cd duedesk-backend
   npm install
   cp ../.env.example .env
   # Edit .env with your configuration
   npm start
   ```

3. **Frontend Setup**
   ```bash
   cd duedesk-dashboard
   npm install
   npm start
   ```

4. **Default Login Credentials**
   - **Username:** admin
   - **Password:** admin123
   - ⚠️ **Change immediately after first login!**

## 🚀 Deployment

### Render (Recommended)

1. **Connect GitHub Repository**
   - Connect your GitHub account to Render
   - Select this repository

2. **Backend Deployment**
   - Create a new Web Service
   - Build Command: `cd duedesk-backend && npm install`
   - Start Command: `cd duedesk-backend && npm start`
   - Environment Variables:
     ```
     NODE_ENV=production
     JWT_SECRET=your-secure-256-bit-secret
     PORT=10000
     ```

3. **Frontend Deployment**
   - Create a new Static Site
   - Build Command: `cd duedesk-dashboard && npm install && npm run build`
   - Publish Directory: `duedesk-dashboard/build`
   - Environment Variables:
     ```
     REACT_APP_API_URL=https://your-backend-url.onrender.com
     ```

### Alternative: Vercel + PlanetScale

For serverless deployment, you'll need to:
1. Deploy frontend to Vercel
2. Use external database (PlanetScale, Supabase, etc.)
3. Deploy API as serverless functions

## 🔒 Security Features

- **JWT Authentication** with secure token generation
- **Password Hashing** using bcrypt with salt rounds
- **Input Validation** for all API endpoints
- **CORS Configuration** for frontend-backend communication
- **SQL Injection Protection** using parameterized queries
- **Environment Variables** for sensitive configuration

## 📊 API Endpoints

### Authentication
- `POST /api/auth/login` - Admin login
- `GET /api/auth/verify` - Verify token
- `POST /api/auth/logout` - Logout

### Customers
- `GET /api/customers` - Get all customers
- `POST /api/customers` - Create new customer
- `GET /api/customers/:id` - Get specific customer
- `PUT /api/customers/:id` - Update customer
- `DELETE /api/customers/:id` - Delete customer

### Payments
- `PATCH /api/customers/:id/payment` - Update payment
- `POST /api/customers/:id/process-payment` - Process payment with different modes

### Dashboard
- `GET /api/dashboard/summary` - Get dashboard statistics
- `GET /api/transactions` - Get transaction history

## 🛡️ Security Recommendations

Before deploying to production:

1. **Change default admin password**
2. **Generate secure JWT secret** (256-bit minimum)
3. **Configure CORS** for your frontend domain only
4. **Enable HTTPS** (automatic on Render)
5. **Set up regular database backups**
6. **Monitor API usage** and implement rate limiting
7. **Keep dependencies updated**

## 🐛 Troubleshooting

**Common Issues:**

1. **Database connection errors**
   - Ensure SQLite file permissions are correct
   - Check if database file exists and is writable

2. **CORS errors**
   - Verify frontend URL in CORS configuration
   - Check API_URL environment variable in frontend

3. **Authentication issues**
   - Verify JWT_SECRET is set correctly
   - Check token expiration settings

## 📝 License

This project is licensed under the ISC License.

## 👨‍💻 Author

**DueDesk Team**
- GitHub: [@AdityaJoshi-14](https://github.com/AdityaJoshi-14)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

---

Built with ❤️ for efficient payment management
