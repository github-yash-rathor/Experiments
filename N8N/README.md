# N8N Workflow Automation Setup

This folder contains a Docker-based N8N setup for workflow automation and integration.

## What is N8N?

N8N is a powerful workflow automation tool that allows you to connect different services and automate tasks without coding. It provides a visual interface to create workflows by connecting nodes that represent different services, APIs, and data transformations.

## Setup Overview

This setup uses Docker Compose to run N8N in a containerized environment with the following configuration:

### Configuration Details

- **Container Name**: `my_n8n`
- **Port Mapping**: `5677:5678` (Access N8N at `http://localhost:5677`)
- **Authentication**: Basic Auth enabled
  - Username: `admin`
  - Password: `changeme` (⚠️ **Change this in production!**)
- **Timezone**: America/New_York
- **Data Persistence**: All N8N data is stored in the `./n8n-data` directory

### File Structure

```
N8N/
├── docker-compose.yaml    # Docker Compose configuration
├── n8n-data/             # Persistent data directory
│   ├── binaryData/       # Binary files and attachments
│   ├── config/           # N8N configuration files
│   ├── database.sqlite   # N8N database
│   ├── git/              # Git integration data
│   ├── nodes/            # Custom nodes and packages
│   └── ssh/              # SSH keys and configurations
└── README.md             # This file
```

## Getting Started

### Prerequisites

- Docker and Docker Compose installed on your system
- Port 5677 available on your machine

### Running N8N

1. **Start the service**:
   ```bash
   cd N8N
   docker-compose up -d
   ```

2. **Access N8N**:
   - Open your browser and go to `http://localhost:5677`
   - Login with:
     - Username: `admin`
     - Password: `changeme`

3. **Stop the service**:
   ```bash
   docker-compose down
   ```

### First Steps

1. **Change the default password**:
   - Go to Settings → User Management
   - Update the admin password to something secure

2. **Explore the interface**:
   - Create your first workflow by clicking "New workflow"
   - Drag and drop nodes to build your automation
   - Use the "Execute Workflow" button to test your workflows

## Common Use Cases

- **API Integrations**: Connect different services and APIs
- **Data Processing**: Transform and move data between systems
- **Notifications**: Send alerts and notifications based on triggers
- **File Operations**: Automate file processing and management
- **Database Operations**: Sync data between different databases
- **Social Media**: Automate posting and monitoring across platforms

## Data Persistence

All your workflows, credentials, and settings are stored in the `n8n-data` directory. This means:
- Your data persists between container restarts
- You can backup your entire N8N setup by copying the `n8n-data` folder
- The database (`database.sqlite`) contains all your workflow definitions and execution history

## Security Considerations

⚠️ **Important Security Notes**:

1. **Change Default Credentials**: The default password `changeme` should be changed immediately
2. **Network Security**: Consider using a reverse proxy (nginx, traefik) for production deployments
3. **Environment Variables**: Store sensitive credentials as environment variables, not in workflows
4. **Backup**: Regularly backup the `n8n-data` directory

## Customization

### Adding Custom Nodes

Custom nodes can be added to the `n8n-data/nodes/` directory. The `package.json` file in this directory manages custom node dependencies.

### Environment Variables

You can modify the `docker-compose.yaml` file to add additional environment variables:

```yaml
environment:
  - N8N_BASIC_AUTH_ACTIVE=true
  - N8N_BASIC_AUTH_USER=admin
  - N8N_BASIC_AUTH_PASSWORD=your_secure_password
  - N8N_HOST=your-domain.com
  - N8N_PORT=5678
  - N8N_PROTOCOL=https
  - WEBHOOK_URL=https://your-domain.com/
```

## Troubleshooting

### Common Issues

1. **Port Already in Use**: If port 5677 is already in use, modify the port mapping in `docker-compose.yaml`
2. **Permission Issues**: Ensure Docker has proper permissions to access the `n8n-data` directory
3. **Container Won't Start**: Check Docker logs with `docker-compose logs n8n`

### Logs

View N8N logs:
```bash
docker-compose logs -f n8n
```

### Reset Everything

To start fresh (⚠️ **This will delete all your workflows and data**):
```bash
docker-compose down
rm -rf n8n-data
docker-compose up -d
```

## Resources

- [N8N Official Documentation](https://docs.n8n.io/)
- [N8N Community Forum](https://community.n8n.io/)
- [N8N GitHub Repository](https://github.com/n8n-io/n8n)
- [Docker Hub N8N Image](https://hub.docker.com/r/n8nio/n8n)

## Support

For issues specific to this setup, check the troubleshooting section above. For N8N-specific questions, refer to the official documentation or community forum.
