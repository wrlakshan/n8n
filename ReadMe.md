# 🚀 Self-Hosted n8n with PostgreSQL & ngrok

This guide provides step-by-step instructions to:

- Set up n8n locally using Docker Compose with a PostgreSQL database.
- Expose your local n8n instance to the internet using ngrok.
- Update n8n to the latest version.

---

## 📁 Project Structure

```
n8n-project/
├── docker-compose.yml
└── README.md
```

---

## 🐳 Prerequisites

Ensure you have the following installed on your system:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [ngrok](https://ngrok.com/download)

---

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/wrlakshan/n8n.git
cd n8n-project
```

> Replace `https://github.com/wrlakshan/n8n.git` with your actual repository URL if applicable.

### 2. Start the Services

Run the following command to start the containers:

```bash
docker-compose up -d
```

This command will:

- Pull the necessary Docker images.
- Create and start the `postgres` and `n8n` containers.
- Set up the volumes for persistent data storage.

### 4. Expose n8n to the Internet Using ngrok

In a new terminal window, run:

```bash
ngrok http --url=whole-eternal-amoeba.ngrok-free.app 80
```

This will generate a public URL (e.g., `https://whole-eternal-amoeba.ngrok-free.app`) that tunnels to your local n8n instance.

> **Note:** Ensure that the generated ngrok URL matches the `N8N_HOST` and `WEBHOOK_URL` specified in your `docker-compose.yml`. If it differs, update the environment variables accordingly and restart the containers.

### 5. Access the n8n Editor

Open your browser and navigate to:

```
https://whole-eternal-amoeba.ngrok-free.app
```

---

## 🔄 Updating n8n to the Latest Version

To update your n8n instance to the latest version, follow these steps:

### 1. Pull the Latest Docker Image

```bash
docker-compose pull
```

This command fetches the latest image of n8n.

### 2. Restart the Containers

```bash
docker-compose down
docker-compose up -d
```

This sequence stops and removes the existing containers, then starts them anew with the updated image.

> **Note:** Your data (workflows, credentials, etc.) is preserved in the Docker volumes (`n8n_data` and `postgres_data`) and will persist across container restarts.

---

## 🛠️ Additional Tips

- **Persistent Data:** Ensure that you do not delete the Docker volumes unless you intend to remove all data.
- **Custom Domains:** For production setups, consider using a custom domain with HTTPS certificates instead of ngrok.
- **Security:** Change the default `admin` credentials to secure your instance.
- **Backups:** Regularly back up your `n8n_data` and `postgres_data` volumes to prevent data loss.

---
