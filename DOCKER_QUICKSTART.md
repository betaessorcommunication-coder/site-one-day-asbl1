# ONE DAY ASBL - Docker Quick Start

## Prerequisites

- Docker: https://docker.com/products/docker-desktop
- Docker Compose: Included with Docker Desktop

## Quick Start (One Command!)

```bash
docker-compose up -d

# Wait 30 seconds for services to start...

# Access:
# Frontend:  http://localhost:3000
# Backend:   http://localhost:5000
# Database:  mongodb://admin:secure_password_change_me@localhost:27017
```

## Services Included

| Service               | Port  | Status                       |
| --------------------- | ----- | ---------------------------- |
| **Frontend** (Nginx)  | 3000  | http://localhost:3000 ✅     |
| **Backend** (Node.js) | 5000  | http://localhost:5000 ✅     |
| **MongoDB**           | 27017 | mongodb://localhost:27017 ✅ |
| **Redis**             | 6379  | redis://localhost:6379 ✅    |

## Common Commands

### Start Services

```bash
docker-compose up -d
```

### Stop Services

```bash
docker-compose down
```

### View Logs

```bash
# All services
docker-compose logs -f

# Specific service
docker-compose logs -f backend
docker-compose logs -f mongodb
```

### Access Database

```bash
docker-compose exec mongodb mongosh -u admin -p
# Password: secure_password_change_me
```

### Rebuild Services

```bash
docker-compose up -d --build
```

### Remove Everything (Clean Slate)

```bash
docker-compose down -v  # -v = remove volumes
```

## Development Workflow

```bash
# 1. Start all services
docker-compose up -d

# 2. Make code changes (auto-reload with nodemon)

# 3. View logs
docker-compose logs -f backend

# 4. Check status
docker-compose ps

# 5. Stop when done
docker-compose down
```

## Environment Variables

Edit `.env` file in `backend/` directory to override:

```env
NODE_ENV=development
MONGODB_URI=mongodb://admin:password@mongodb:27017/one-day-asbl?authSource=admin
FLUTTERWAVE_PUBLIC_KEY=your_test_key
```

## Troubleshooting

### Port Already in Use

```bash
# Check what's using port 5000
lsof -i :5000

# Or use different ports in docker-compose.yml
ports:
  - "5001:5000"  # Changed from 5000 to 5001
```

### Services Won't Start

```bash
# Check logs
docker-compose logs backend

# Rebuild services
docker-compose up -d --build --force-recreate
```

### Database Connection Error

```bash
# Ensure MongoDB is healthy
docker-compose ps

# Check MongoDB status
docker-compose exec mongodb mongosh --eval "db.adminCommand('ping')"
```

## Production Deployment

For production, use environment-specific configs:

```bash
# Production with environment file
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

Create `docker-compose.prod.yml`:

```yaml
version: "3.8"
services:
  backend:
    environment:
      NODE_ENV: production
      FLUTTERWAVE_PUBLIC_KEY: FLWPUBK_LIVE_xxxxx
      FLUTTERWAVE_SECRET_KEY: FLWSECK_LIVE_xxxxx
```

---

**Easy deployment with Docker! 🐳**
