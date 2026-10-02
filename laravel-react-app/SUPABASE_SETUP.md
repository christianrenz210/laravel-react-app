# Supabase Database Setup Guide

## 📋 Prerequisites
- Supabase account ([sign up here](https://supabase.com))
- Your Laravel application ready for deployment

## 🚀 Step-by-Step Setup

### 1. Create Supabase Project

1. Go to [Supabase Dashboard](https://supabase.com/dashboard)
2. Click "New Project"
3. Fill in:
   - **Name**: `laravel-react-app` (or your preferred name)
   - **Database Password**: Generate a strong password (save it!)
   - **Region**: Choose closest to your users
   - **Pricing Plan**: Free tier is fine for testing

4. Wait for project to be provisioned (2-3 minutes)

### 2. Get Database Credentials

1. In your Supabase project, go to **Project Settings** (gear icon)
2. Navigate to **Database** section
3. Find the **Connection String** section
4. You'll see connection details:
   ```
   Host: db.xxxxxxxxxxxxx.supabase.co
   Database name: postgres
   Port: 5432
   User: postgres
   Password: [your-password]
   ```

### 3. Configure Laravel Environment

Update your deployment platform (Railway/Heroku) environment variables:

```env
DB_CONNECTION=pgsql
DB_HOST=db.xxxxxxxxxxxxx.supabase.co
DB_PORT=5432
DB_DATABASE=postgres
DB_USERNAME=postgres
DB_PASSWORD=your-supabase-password
```

### 4. Connection String Format

Alternative: Use the full connection string:
```
postgresql://postgres:your-password@db.xxxxxxxxxxxxx.supabase.co:5432/postgres
```

### 5. Run Migrations

Once deployed, your Laravel app will automatically run:
```bash
php artisan migrate --force
```

This creates these tables:
- ✅ users
- ✅ password_reset_tokens  
- ✅ sessions
- ✅ cache
- ✅ cache_locks
- ✅ jobs
- ✅ job_batches
- ✅ failed_jobs

### 6. Verify in Supabase

1. Go to **Table Editor** in Supabase
2. You should see all migrated tables
3. Check **SQL Editor** to run custom queries if needed

## 🔒 Security Best Practices

1. **Never commit** database credentials to Git
2. Use **environment variables** for all secrets
3. Enable **Row Level Security (RLS)** in Supabase if needed
4. Use **SSL connections** (enabled by default in Supabase)
5. Rotate passwords regularly

## 🐛 Troubleshooting

### Connection Refused
- Check if Supabase project is active
- Verify firewall allows connections to Supabase IP ranges
- Confirm port 5432 is accessible

### Migration Errors
```bash
# Clear config cache
php artisan config:clear

# Try migrations again
php artisan migrate --force
```

### SSL Errors
Add to your database config:
```php
'pgsql' => [
    // ... other config
    'sslmode' => 'require',
],
```

## 📊 Supabase Features You Can Use

- **Table Editor**: Visual database management
- **SQL Editor**: Run custom queries
- **Database Webhooks**: Trigger actions on data changes
- **Realtime**: Subscribe to database changes
- **Storage**: File uploads (S3-compatible)
- **Auth**: Can integrate with Laravel Sanctum

## 🔗 Useful Links

- [Supabase Dashboard](https://supabase.com/dashboard)
- [Supabase Documentation](https://supabase.com/docs)
- [Laravel PostgreSQL Guide](https://laravel.com/docs/11.x/database#postgresql)
