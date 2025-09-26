# Installation Guide

This guide provides step-by-step instructions for setting up the Real-Time Disease Tracking System locally and in production.

## Prerequisites

### System Requirements
- **Operating System**: Windows 10+, macOS 10.14+, or Linux (Ubuntu 18.04+)
- **Python**: Version 3.8 or higher
- **Database**: MySQL 5.7 or higher
- **Memory**: Minimum 4GB RAM (8GB recommended for development)
- **Storage**: At least 2GB free space

### Required Software
- **Git**: For version control
- **Python pip**: Package manager (usually comes with Python)
- **MySQL**: Database server
- **Docker** (optional): For containerized deployment

## Local Development Setup

### 1. Clone the Repository

```bash
git clone https://github.com/chowhanm25/real-time-disease-tracking.git
cd real-time-disease-tracking
```

### 2. Set Up Python Environment

Create and activate a virtual environment:

**Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

**macOS/Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Python Dependencies

```bash
pip install -r requirements.txt
```

### 4. Database Setup

#### MySQL Installation
1. Download and install MySQL from [mysql.com](https://dev.mysql.com/downloads/mysql/)
2. Create a new database:

```sql
CREATE DATABASE disease_tracking;
CREATE USER 'dt_user'@'localhost' IDENTIFIED BY 'your_password';
GRANT ALL PRIVILEGES ON disease_tracking.* TO 'dt_user'@'localhost';
FLUSH PRIVILEGES;
```

#### Configure Django Settings
1. Copy the example environment file:
```bash
cp .env.example .env
```

2. Update the `.env` file with your database credentials:
```env
DB_NAME=disease_tracking
DB_USER=dt_user
DB_PASSWORD=your_password
DB_HOST=localhost
DB_PORT=3306
SECRET_KEY=your_django_secret_key
DEBUG=True
```

### 5. Run Database Migrations

```bash
python manage.py migrate
```

### 6. Create a Superuser

```bash
python manage.py createsuperuser
```

### 7. Load Initial Data (Optional)

```bash
python manage.py loaddata initial_data.json
```

### 8. Start the Development Server

```bash
python manage.py runserver
```

The application will be available at `http://localhost:8000`

## Docker Deployment

### 1. Prerequisites
- Docker installed and running
- Docker Compose installed

### 2. Environment Configuration
Create a `.env` file with production settings:

```env
DB_NAME=disease_tracking
DB_USER=dt_user
DB_PASSWORD=secure_password_here
DB_HOST=db
DB_PORT=3306
SECRET_KEY=your_production_secret_key
DEBUG=False
ALLOWED_HOSTS=localhost,127.0.0.1,your-domain.com
```

### 3. Build and Run

```bash
# Build the images
docker-compose build

# Start the services
docker-compose up -d

# Run database migrations
docker-compose exec web python manage.py migrate

# Create superuser
docker-compose exec web python manage.py createsuperuser
```

### 4. Access the Application
- **Main Application**: http://localhost:8000
- **Admin Panel**: http://localhost:8000/admin

## Production Deployment (AWS EC2)

### 1. EC2 Instance Setup
1. Launch an EC2 instance (t2.medium or larger recommended)
2. Configure security groups to allow HTTP (80), HTTPS (443), and SSH (22)
3. Install Docker and Docker Compose on the instance

### 2. Domain and SSL Configuration
1. Point your domain to the EC2 instance IP
2. Install and configure Nginx as reverse proxy
3. Set up SSL certificates using Let's Encrypt

### 3. Environment Variables
Create production environment file:

```env
DB_NAME=disease_tracking_prod
DB_USER=dt_prod_user
DB_PASSWORD=very_secure_password
DB_HOST=localhost
DB_PORT=3306
SECRET_KEY=production_secret_key_here
DEBUG=False
ALLOWED_HOSTS=yourdomain.com,www.yourdomain.com
```

## Common Issues and Troubleshooting

### Database Connection Issues
```bash
# Check MySQL service status
sudo systemctl status mysql

# Restart MySQL if needed
sudo systemctl restart mysql
```

### Permission Errors
```bash
# Fix file permissions
chmod +x manage.py
chown -R $USER:$USER .
```

### Port Already in Use
```bash
# Find and kill process using port 8000
lsof -ti:8000 | xargs kill -9
```

## Testing the Installation

### 1. Basic Functionality Test
1. Visit `http://localhost:8000`
2. Register a new user account
3. Log in successfully
4. Submit a test disease report
5. Verify the report appears on the map

### 2. Admin Panel Test
1. Visit `http://localhost:8000/admin`
2. Log in with superuser credentials
3. Create test data for diseases, symptoms, and conditions

### 3. API Endpoints Test
```bash
# Test API availability
curl http://localhost:8000/api/diseases/
curl http://localhost:8000/api/reports/
```

## Performance Optimization

### 1. Database Optimization
```sql
-- Add indexes for better performance
CREATE INDEX idx_reports_date ON disease_reports(created_at);
CREATE INDEX idx_reports_location ON disease_reports(country, city);
```

### 2. Static Files Configuration
```bash
# Collect static files for production
python manage.py collectstatic --noinput
```

## Security Considerations

### 1. Environment Variables
- Never commit `.env` files to version control
- Use strong, unique passwords
- Regularly rotate secret keys

### 2. Database Security
- Use dedicated database user with minimal privileges
- Enable MySQL SSL connections in production
- Regular security updates

## Support

For installation support:
1. Check the troubleshooting section above
2. Review Django logs for error details
3. Create an issue in the GitHub repository
4. Contact the development team

## Next Steps

After successful installation:
1. Read the [User Manual](USER_MANUAL.md)
2. Review the [API Documentation](API_DOCUMENTATION.md)
3. Explore the [Testing Guide](TESTING.md)