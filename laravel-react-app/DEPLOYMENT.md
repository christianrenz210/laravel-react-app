# Deployment Guide

This Laravel + React (Inertia.js) application requires both backend and frontend deployment.

## 🚀 Recommended: Railway Deployment (Full Stack)

Railway supports PHP applications with PostgreSQL databases out of the box.

### Steps:

1. **Create Supabase Database**
   - Go to [Supabase](https://supabase.com/) and create a new project
   - Navigate to Project Settings > Database
   - Copy the connection details:
     - Host
     - Database name
     - Port (5432)
     - User
     - Password

2. **Deploy to Railway**
   - Go to [Railway](https://railway.app/)
   - Click "New Project" > "Deploy from GitHub repo"
   - Select `christianrenz210/laravel-react-app`
   - Railway will auto-detect Laravel and deploy

3. **Configure Environment Variables in Railway**
   ```
   APP_NAME=Laravel React App
   APP_ENV=production
   APP_KEY=base64:DD/4GMp61bixcoa7RuyE5iWShklvOVdZTKTryhjsIqQ=
   APP_DEBUG=false
   APP_URL=https://your-app.railway.app
   
   DB_CONNECTION=pgsql
   DB_HOST=your-supabase-host.supabase.co
   DB_PORT=5432
   DB_DATABASE=postgres
   DB_USERNAME=postgres
   DB_PASSWORD=your-supabase-password
   
   SESSION_DRIVER=database
   QUEUE_CONNECTION=database
   CACHE_STORE=database
   ```

4. **Generate New APP_KEY**
   ```bash
   php artisan key:generate --show
   ```
   Copy the output and set it as APP_KEY in Railway

5. **Deploy**
   - Railway will automatically build and deploy
   - Migrations will run automatically on startup
   - Access your app at the generated Railway URL

## 📦 Alternative: Vercel (Frontend Only - Not Recommended for Laravel)

⚠️ **Note**: Vercel doesn't support PHP runtimes well. This setup only serves static assets.

If you want to use Vercel, you'll need:
1. Deploy backend to Railway/Heroku/Laravel Cloud
2. Use Vercel only for CDN/static assets
3. Configure CORS on backend

## 🗄️ Database Migration

The app includes these migrations:
- Users table (authentication)
- Cache table
- Jobs queue table
- Sessions table
- Password reset tokens

Migrations will run automatically during deployment with:
```bash
php artisan migrate --force
```

## 🔧 Post-Deployment

1. Test authentication flows
2. Verify database connections
3. Check logs in Railway dashboard
4. Update APP_URL in environment variables

## 📝 Files Created for Deployment

- `Procfile` - Heroku deployment
- `railway.json` - Railway configuration
- `nixpacks.toml` - Railway build configuration
- `vercel.json` - Vercel configuration (static only)
- `.env.production` - Production environment template

## 🔗 Useful Commands

```bash
# Build frontend assets
npm run build

# Run migrations
php artisan migrate --force

# Clear and cache config
php artisan config:cache
php artisan route:cache
php artisan view:cache

# Clear all caches
php artisan optimize:clear
```
