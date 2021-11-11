# Databases (GCP)
 
---

## Creating a Cloud SQL instance

### CLI: Creating a Cloud SQL instance
```bash
gcloud sql instances create flights \
    --tier=db-n1-standard-1 --activation-policy=ALWAYS
```
### Setting a root password for the Cloud SQL instance
```bash
gcloud sql users set-password root --host % --instance flights \
 --password Passw0rd
```

### Obtaining an env variable for Cloud shell address
```bash
export ADDRESS=$(wget -qO - http://ipecho.net/plain)/32
```

### Allowlist the Cloud shell instance for management access to SQL instance
```bash
gcloud sql instances patch flights --authorized-networks $ADDRESS
```

### Get IP address of your Cloud SQL instance
```bash
MYSQLIP=$(gcloud sql instances describe \
flights --format="value(ipAddresses.ipAddress)")
```

### Connecting to the SQL CLI
```bash
mysql --host=$MYSQLIP --user=root  --password
```

### Accessing Cloud SQL Second Generation Instances with Cloud SQL Proxy
- No need to allowlist IP addresses
- No need to configure SSL
- Secure Connections: Proxy automatically encrypts traffic to/from database using TLS 1.2
- Easier connection management

#### Installing Cloud SQL Proxy
```bash
wget https://dl.google.com/cloudsql/cloud_sql_proxy.linux.amd64 -O cloud_sql_proxy

chmod +x cloud_sql_proxy
```

#### Test connection to database
```bash
export GOOGLE_PROJECT=$(gcloud config get-value project)
```

Obtain MySQL database and connection name
```bash
MYSQL_DB_NAME=$(terraform output -json | jq -r '.instance_name.value')
MYSQL_CONN_NAME="${GOOGLE_PROJECT}:us-central1:${MYSQL_DB_NAME}"
```

Start the Cloud SQL Proxy
```bash
./cloud_sql_proxy -instances=${MYSQL_CONN_NAME}=tcp:3306
```

On a new command terminal, connect to the instance
```bash
echo MYSQL_PASSWORD=$(terraform output -json | jq -r '.generated_user_password.value')

mysql -udefault -p --host 127.0.0.1 default
```

