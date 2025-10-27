# System Architecture

## Overview
DevOps Simulator follows a microservices architecture designed for high availability, scalability, and flexibility across both production and development environments.

---

## 🏭 Production Architecture

### Components

#### 1. Application Server
- **Technology**: Node.js + Express
- **Port**: 8080
- **Scaling**: Horizontal auto-scaling enabled

#### 2. Database Layer
- **Database**: PostgreSQL 14
- **Configuration**: Master-slave replication
- **Backup**: Daily automated backups

#### 3. Monitoring System
- **Tool**: Prometheus + Grafana
- **Metrics**: CPU, Memory, Disk, Network
- **Alerts**: Email notifications for critical issues

### Deployment Strategy
- **Method**: Rolling updates
- **Zero-downtime**: ✅ Yes
- **Rollback**: Automated on failure

### Security
- SSL/TLS encryption  
- Database connection encryption  
- Regular security audits  

---

## 🧩 Development Architecture (Experimental)

**Version:** Development (2.0.0-beta)  
**Purpose:** Local testing, debugging, and feature experimentation.

### Components

#### 1. Application Server
- **Technology**: Node.js + Express (with hot reload)
- **Port**: 3000
- **Scaling**: Manual (single instance)
- **Debug**: Chrome DevTools on port 9229

#### 2. Database Layer
- **Database**: PostgreSQL 14 (local)
- **Configuration**: Single instance (no replication)
- **Backup**: Manual only
- **Seeding**: Auto-seed with test data on startup

#### 3. Monitoring System
- **Tool**: Console logging + Prometheus (optional)
- **Metrics**: CPU, Memory, Disk, Network, Build time
- **Alerts**: Console warnings (no email)
- **Dashboard**: In-development local dashboard

#### 4. Container Orchestration (New)
- **Tool**: Docker Compose
- **Services**: App, Database, Redis cache
- **Volume Mounts**: Code directory for hot reload

#### 5. Authentication System (Beta)
- **Method**: OAuth2 + JWT
- **Providers**: Google, GitHub
- **Sessions**: Redis-based session storage

### Deployment Strategy
- **Method**: Docker Compose hot reload
- **Zero-downtime**: ❌ Not applicable
- **Rollback**: Use Git checkout of previous commit

### Development Workflow
1. Make code changes  
2. Auto-reload triggers rebuild  
3. Run unit tests  
4. Observe console logs  
5. Commit when ready  

### Security
- SSL/TLS disabled (local only)  
- Database credentials in plain text (dev only)  
- CORS enabled for all origins  
- Debug endpoints exposed  

### Experimental Features
⚠️ **Under testing:**
- Multi-cloud deployment  
- AI-powered log analysis  
- Automatic rollback on anomaly detection  

---

✅ *This unified document ensures both environments (Production + Development) are clearly documented and comparable.*
