# Experiments

This repository contains various experimental projects and tools for testing and learning purposes.

## Projects

### N8N Workflow Automation

The `N8N/` folder contains a Docker-based setup for N8N, a powerful workflow automation tool that allows you to connect different services and automate tasks without coding.

**Quick Start:**
- Navigate to the `N8N/` directory
- Run `docker-compose up -d` to start the service
- Access N8N at `http://localhost:5677`
- Use the credentials configured in the docker-compose.yaml file

**Features:**
- Visual workflow builder with drag-and-drop interface
- 200+ pre-built integrations with popular services
- Custom node support for specialized workflows
- Data persistence with SQLite database
- Basic authentication for security

**Documentation:**
For detailed setup instructions, configuration options, troubleshooting, and usage examples, see the comprehensive [N8N README](./N8N/README.md).

**Use Cases:**
- API integrations and data synchronization
- Automated notifications and alerts
- File processing and data transformation
- Social media automation
- Database operations and ETL processes