# Laravel + React (Inertia.js) Application

Modern full-stack application built with Laravel 13, React 18, Inertia.js, and Tailwind CSS.

## 🚀 Deployment Ready

This application is configured for deployment on multiple platforms with Supabase PostgreSQL database.

### Quick Deploy Options:

1. **Railway (Recommended)** - Full PHP + PostgreSQL support
2. **Heroku** - Classic platform
3. **Vercel** - Static assets only (requires separate backend)

📖 **See [DEPLOYMENT.md](DEPLOYMENT.md) for detailed deployment instructions**  
📖 **See [SUPABASE_SETUP.md](SUPABASE_SETUP.md) for database setup**

## 🛠️ Tech Stack

- **Backend**: Laravel 13 (PHP 8.3)
- **Frontend**: React 18 + Inertia.js
- **Styling**: Tailwind CSS 3
- **Build Tool**: Vite 8
- **Database**: PostgreSQL (Supabase) / SQLite (local)
- **Authentication**: Laravel Breeze + Sanctum

## 📋 Features

- ✅ User Authentication (Login/Register)
- ✅ Dashboard with Sidebar Navigation
- ✅ Server-Side Rendering with Inertia.js
- ✅ Responsive Design
- ✅ Session Management
- ✅ Queue System
- ✅ Cache System

## 🏃 Local Development

### Prerequisites
- PHP 8.3+
- Composer
- Node.js 20+
- SQLite (default) or PostgreSQL

### Installation

1. Clone the repository:
```bash
git clone https://github.com/christianrenz210/laravel-react-app.git
cd laravel-react-app
```

2. Install dependencies:
```bash
composer install
npm install
```

3. Setup environment:
```bash
cp .env.example .env
php artisan key:generate
```

4. Create database:
```bash
touch database/database.sqlite
php artisan migrate
```

5. Build frontend assets:
```bash
npm run build
# or for development with hot reload
npm run dev
```

6. Start the server:
```bash
php artisan serve
```

Visit: `http://localhost:8000`

## 📁 Project Structure

```
laravel-react-app/
├── app/                    # Laravel application logic
├── resources/
│   ├── js/                # React components
│   │   ├── Components/   # Reusable React components
│   │   ├── Layouts/      # Page layouts
│   │   └── Pages/        # Inertia pages
│   └── css/              # Styles
├── routes/                # Laravel routes
├── database/
│   └── migrations/       # Database migrations
├── public/               # Public assets
└── config/               # Configuration files
```

## 🗄️ Database Migrations

The application includes these database tables:
- `users` - User authentication
- `sessions` - Session management
- `password_reset_tokens` - Password resets
- `cache` - Application cache
- `jobs` - Queue jobs
- `failed_jobs` - Failed queue jobs

## 🔧 Available Commands

```bash
# Development
php artisan serve              # Start Laravel server
npm run dev                    # Start Vite dev server

# Production Build
npm run build                  # Build frontend assets
php artisan config:cache       # Cache configuration
php artisan route:cache        # Cache routes
php artisan view:cache         # Cache views

# Database
php artisan migrate            # Run migrations
php artisan migrate:fresh      # Fresh migration
php artisan db:seed            # Seed database

# Maintenance
php artisan optimize:clear     # Clear all caches
php artisan queue:work         # Process queue jobs
php artisan tinker             # Laravel REPL
```

## 🌐 Deployment

### Railway Deployment (Recommended)

1. Create a [Supabase](https://supabase.com) database
2. Deploy to [Railway](https://railway.app)
3. Configure environment variables
4. Migrations run automatically

### Environment Variables

```env
APP_NAME="Laravel React App"
APP_ENV=production
APP_KEY=base64:your-key-here
APP_DEBUG=false
APP_URL=https://your-app.railway.app

DB_CONNECTION=pgsql
DB_HOST=db.xxxxx.supabase.co
DB_PORT=5432
DB_DATABASE=postgres
DB_USERNAME=postgres
DB_PASSWORD=your-password
```

## 📝 Documentation

- [DEPLOYMENT.md](DEPLOYMENT.md) - Complete deployment guide
- [SUPABASE_SETUP.md](SUPABASE_SETUP.md) - Database setup guide
- [SIDEBAR_IMPLEMENTATION.md](SIDEBAR_IMPLEMENTATION.md) - Sidebar feature docs

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

## 🔗 Links

- **Repository**: https://github.com/christianrenz210/laravel-react-app
- **Laravel**: https://laravel.com
- **React**: https://react.dev
- **Inertia.js**: https://inertiajs.com
- **Tailwind CSS**: https://tailwindcss.com
