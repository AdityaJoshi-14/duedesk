# 🚂 Railway Deployment Guide for DueDesk

## Prerequisites
- GitHub repository with your code (✅ Done)
- Railway account (sign up at https://railway.app)

## 🚀 Step-by-Step Deployment

### 1. Sign up for Railway
1. Go to https://railway.app
2. Click "Login" and choose "Login with GitHub"
3. Authorize Railway to access your repositories

### 2. Deploy Backend (API Server)

#### Create New Project:
1. Click "New Project"
2. Select "Deploy from GitHub repo"
3. Choose `AdityaJoshi-14/duedesk`
4. Select "Deploy Now"

#### Configure Backend Service:
1. Railway will auto-detect Node.js
2. Set **Root Directory**: `duedesk-backend`
3. **Environment Variables** (Add these in Railway dashboard):
   ```
   NODE_ENV=production
   JWT_SECRET=your-super-secure-256-bit-secret-key-here
   PORT=3000
   ```

#### Generate JWT Secret:
```bash
# Use this command to generate a secure JWT secret:
node -e "console.log(require('crypto').randomBytes(64).toString('hex'))"
```

### 3. Deploy Frontend (React App)

#### Add Frontend Service:
1. In your Railway project, click "+ New Service"
2. Select "GitHub Repo"
3. Choose the same `duedesk` repository
4. Set **Root Directory**: `duedesk-dashboard`

#### Configure Frontend Service:
1. **Build Command**: `npm run build`
2. **Start Command**: `npx serve -s build -p $PORT`
3. **Environment Variables**:
   ```
   REACT_APP_API_URL=https://your-backend-service-url.railway.app
   ```

### 4. Domain Configuration

#### Backend URL:
- Railway provides: `https://your-backend-service.railway.app`
- Custom domain: Available in Railway dashboard

#### Frontend URL:
- Railway provides: `https://your-frontend-service.railway.app`
- Custom domain: Available in Railway dashboard

### 5. Environment Variables Setup

#### Backend Variables:
```bash
NODE_ENV=production
JWT_SECRET=64-character-hex-string-from-crypto-random-bytes
PORT=3000
```

#### Frontend Variables:
```bash
REACT_APP_API_URL=https://duedesk-backend-abc123.railway.app
```

### 6. Database Considerations

#### SQLite on Railway:
- ✅ Railway supports persistent file storage
- ✅ Your `customers.db` will persist between deployments
- ✅ Automatic backups available
- ⚠️ For high traffic, consider PostgreSQL upgrade

#### Backup Strategy:
```bash
# Railway CLI backup (install railway CLI first)
railway run --service backend "sqlite3 customers.db .dump" > backup.sql
```

### 7. Post-Deployment Checklist

#### Test Your Application:
1. **Backend Health Check**: `https://your-backend.railway.app/api/health`
2. **Frontend Access**: `https://your-frontend.railway.app`
3. **Login Test**: Use default credentials (admin/admin123)
4. **IMPORTANT**: Change default password immediately!

#### Security Setup:
1. **Change admin password** through the app
2. **Verify JWT secret** is properly set
3. **Check CORS configuration** matches your frontend URL
4. **Test payment processing** functionality

### 8. Automatic Deployments

#### GitHub Integration:
- ✅ Railway automatically deploys on `git push`
- ✅ Both services update independently
- ✅ Rollback available if needed

#### Deployment Triggers:
```bash
# Any push to main branch triggers deployment
git add .
git commit -m "Update: feature description"
git push origin main
```

### 9. Monitoring & Logs

#### Railway Dashboard:
- Real-time logs for both services
- Resource usage monitoring
- Deploy history and rollbacks
- Environment variable management

#### Health Monitoring:
- Backend health endpoint: `/api/health`
- Railway provides uptime monitoring
- Email alerts for service issues

### 10. Scaling & Performance

#### Free Tier Limits:
- 500 hours/month (both services)
- 1GB RAM per service
- 1GB storage
- Perfect for development/small production

#### Upgrade Options:
- **Pro Plan**: $20/month
- **Unlimited usage**
- **More RAM and storage**
- **Priority support**

### 11. Troubleshooting

#### Common Issues:

**Build Failures:**
```bash
# Check Node.js version in logs
# Ensure package.json has correct engines field
```

**Database Connection:**
```bash
# Verify file permissions
# Check SQLite file path in logs
```

**CORS Errors:**
```bash
# Update REACT_APP_API_URL in frontend
# Check backend CORS configuration
```

**Environment Variables:**
```bash
# Verify all required env vars are set
# Check for typos in variable names
```

### 12. Railway CLI (Optional)

#### Install Railway CLI:
```bash
npm install -g @railway/cli
railway login
railway link
```

#### Useful Commands:
```bash
railway status          # Check service status
railway logs            # View logs
railway shell           # Access service shell
railway run node        # Run commands in service context
```

## 🎉 Success!

Once deployed:
1. **Backend URL**: `https://duedesk-backend-xyz.railway.app`
2. **Frontend URL**: `https://duedesk-frontend-xyz.railway.app`
3. **Admin Login**: admin/admin123 (change immediately!)

## 💡 Pro Tips

1. **Use Railway's built-in metrics** to monitor performance
2. **Set up custom domains** for professional appearance
3. **Enable automatic deployments** for continuous delivery
4. **Use Railway's environment branching** for staging environments
5. **Monitor your usage** to stay within free tier limits

## 🆘 Need Help?

- Railway Documentation: https://docs.railway.app
- Railway Discord: https://discord.gg/railway
- Railway Status: https://status.railway.app

Happy deploying! 🚀
