# Laravel Codespace Setup Guide

This repository is configured with GitHub Codespaces for easy development. The setup includes PHP 8.2, MySQL 8.0, Composer, and all necessary tools for Laravel development.

## 🚀 Quick Start

1. **Create Codespace**

    - Click the "Code" button on GitHub
    - Select "Codespaces" tab
    - Click "Create codespace on development"

2. **Wait for Setup**

    - The codespace will automatically install all dependencies
    - Setup takes about 2-3 minutes
    - Watch the terminal for setup progress

3. **Start Development Server**

    ```bash
    # Navigate to your Laravel project directory
    cd project  # or wherever your Laravel files are located

    # Start the development server
    php artisan serve --host=0.0.0.0 --port=8000
    ```

4. **Access Your Application**
    - Laravel App: `http://localhost:8000`
    - phpMyAdmin: `http://localhost:8080`

## 📁 Project Structure

This setup assumes your Laravel project is in a subdirectory, not in the repository root. Common locations:

- `/project/`
- `/app/`
- `/src/`

The setup script will automatically detect your Laravel project location.

## 🛠️ Included Tools

- **PHP 8.2** with common extensions
- **Composer** (latest version)
- **Node.js & NPM** (LTS version)
- **MySQL 8.0** database
- **phpMyAdmin** for database management
- **Laravel Artisan** CLI
- **VS Code extensions** for PHP/Laravel development

## 🗄️ Database Configuration

The MySQL database is automatically configured with:

- **Database**: `laravel_db`
- **Username**: `laravel_user`
- **Password**: `laravel_password`
- **Host**: `mysql` (Docker service name)
- **Port**: `3306`

## ⚙️ Environment Variables

Your `.env` file will be automatically created with the correct database settings. If you have an `.env.example` file, it will be copied. Otherwise, a basic configuration will be generated.

## 🔧 Common Commands

```bash
# Navigate to Laravel project
cd project  # Adjust path as needed

# Install dependencies
composer install
npm install

# Database operations
php artisan migrate
php artisan db:seed
php artisan migrate:fresh --seed

# Laravel development
php artisan serve --host=0.0.0.0 --port=8000
php artisan tinker

# Frontend development
npm run dev
npm run build
npm run watch

# Cache management
php artisan config:cache
php artisan route:cache
php artisan view:cache
php artisan cache:clear
```

## 🐛 Troubleshooting

### Database Connection Issues

```bash
# Check if MySQL is running
docker ps

# Restart MySQL service
docker-compose restart mysql

# Check database connection
php artisan tinker
DB::connection()->getPdo();
```

### Permission Issues

```bash
# Fix storage permissions
sudo chown -R vscode:www-data storage bootstrap/cache
sudo chmod -R 775 storage bootstrap/cache
```

### Missing Dependencies

```bash
# Reinstall PHP dependencies
composer install --no-cache

# Reinstall Node dependencies
npm ci
```

## 🔒 Security Notes

- This setup is for development only
- Default passwords are used for convenience
- Don't use these configurations in production
- Change database credentials before deploying

## 📝 Customization

### Adding PHP Extensions

Edit the `Dockerfile` and add to the `docker-php-ext-install` section:

```dockerfile
RUN docker-php-ext-install \
    pdo_mysql \
    mbstring \
    # Add your extensions here
```

### Adding VS Code Extensions

Edit `.devcontainer/devcontainer.json`:

```json
{
    "customizations": {
        "vscode": {
            "extensions": ["existing.extension", "your.new.extension"]
        }
    }
}
```

### Modifying Database Settings

Edit `docker-compose.yml` to change MySQL configuration:

```yaml
mysql:
    environment:
        MYSQL_DATABASE: your_db_name
        MYSQL_USER: your_username
        MYSQL_PASSWORD: your_password
```

## 🤝 Support

If you encounter issues:

1. Check the setup logs in the terminal
2. Verify your Laravel project structure
3. Ensure all required files exist (composer.json, etc.)
4. Try rebuilding the codespace if problems persist

---

**Happy coding! 🎉**

# 📁 File Placement Guide for Codespace Configuration

## 🎯 Repository Structure

Based on your description that the Laravel project is **NOT in the root** but in a subdirectory, here's exactly where to place each file:

```
your-repository-root/
├── .devcontainer/                    ← CREATE THIS FOLDER
│   ├── devcontainer.json            ← Configuration file #1
│   ├── docker-compose.yml           ← Configuration file #2
│   ├── Dockerfile                   ← Configuration file #3
│   └── setup.sh                     ← Configuration file #4
├── project/                         ← YOUR LARAVEL PROJECT FOLDER
│   ├── app/
│   ├── config/
│   ├── database/
│   ├── resources/
│   ├── routes/
│   ├── storage/
│   ├── composer.json                ← Laravel's composer.json
│   ├── artisan                      ← Laravel's artisan command
│   ├── .env.example                 ← Laravel's environment example
│   └── ... (other Laravel files)
├── README-CODESPACE.md              ← Documentation file
├── README.md                        ← Your existing README
└── ... (other repository files)
```

## 🚀 Step-by-Step Instructions

### Step 1: Create the .devcontainer Folder

In your repository root (same level as your project folder), create a new folder called `.devcontainer`:

```bash
mkdir .devcontainer
```

### Step 2: Create Each Configuration File

Navigate to the `.devcontainer` folder and create these files:

#### File 1: `.devcontainer/devcontainer.json`

```bash
touch .devcontainer/devcontainer.json
```

Copy the content from the first artifact (devcontainer.json).

#### File 2: `.devcontainer/docker-compose.yml`

```bash
touch .devcontainer/docker-compose.yml
```

Copy the content from the second artifact (docker-compose.yml).

#### File 3: `.devcontainer/Dockerfile`

```bash
touch .devcontainer/Dockerfile
```

Copy the content from the third artifact (Dockerfile).

#### File 4: `.devcontainer/setup.sh`

```bash
touch .devcontainer/setup.sh
chmod +x .devcontainer/setup.sh
```

Copy the content from the fourth artifact (setup.sh). **Important**: Make it executable with `chmod +x`.

### Step 3: Create Documentation (Optional)

In your repository root:

```bash
touch README-CODESPACE.md
```

Copy the content from the README artifact.

## 🔧 Alternative Project Folder Names

If your Laravel project is in a different folder name, the setup script will automatically detect it. Common variations:

```
your-repository-root/
├── .devcontainer/          ← Configuration files go here
├── app/                    ← Laravel project here
└── ...

# OR

your-repository-root/
├── .devcontainer/          ← Configuration files go here
├── src/                    ← Laravel project here
└── ...

# OR

your-repository-root/
├── .devcontainer/          ← Configuration files go here
├── sistema-informasi/      ← Laravel project here (custom name)
└── ...
```

## 💡 Quick Commands for File Creation

If you're using terminal/command line, you can create all files at once:

```bash
# Create .devcontainer directory
mkdir .devcontainer

# Create all required files
touch .devcontainer/devcontainer.json
touch .devcontainer/docker-compose.yml
touch .devcontainer/Dockerfile
touch .devcontainer/setup.sh
touch README-CODESPACE.md

# Make setup script executable
chmod +x .devcontainer/setup.sh
```

## ✅ Verification Checklist

After creating the files, verify your structure looks like this:

- [ ] `.devcontainer/` folder exists in repository root
- [ ] `.devcontainer/devcontainer.json` exists
- [ ] `.devcontainer/docker-compose.yml` exists
- [ ] `.devcontainer/Dockerfile` exists
- [ ] `.devcontainer/setup.sh` exists and is executable
- [ ] Your Laravel project folder exists (project/, app/, src/, etc.)
- [ ] Laravel's `composer.json` exists in the project subfolder

## 🚨 Important Notes

1. **Case Sensitive**: The folder name must be exactly `.devcontainer` (with the dot)
2. **Repository Root**: The `.devcontainer` folder goes in the repository root, NOT inside your Laravel project folder
3. **Permissions**: Make sure `setup.sh` is executable (`chmod +x .devcontainer/setup.sh`)
4. **Git**: Don't forget to commit these files to your repository

## 🎯 Final Structure Example

For the repository `gedeadiputra31/sistem-informasi-idep`, it should look like:

```
sistem-informasi-idep/
├── .devcontainer/
│   ├── devcontainer.json
│   ├── docker-compose.yml
│   ├── Dockerfile
│   └── setup.sh
├── project/                 ← Your Laravel files here
│   ├── app/
│   ├── composer.json
│   ├── artisan
│   └── ...
└── README-CODESPACE.md
```

Once you've placed all files correctly, commit and push to your `development` branch, then create a Codespace from GitHub!
