```bash
sudo apt update
sudo apt -y upgrade
sudo wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/20.04/mssql-server-preview.list)"
sudo apt-get install -y mssql-server
sudo /opt/mssql/bin/mssql-conf setup
```



## INSTALLING MSSQL DATABASE (SQL Server 2022) ON UBUNTU

### 1. Download the public key, convert from ASCII to GPG format, and write it to the required location 
```bash
curl -fsSL https://packages.microsoft.com/keys/microsoft.asc | sudo gpg --dearmor -o /usr/share/keyrings/microsoft-prod.gpg
```


### If you receive a warning about the public key not being available, you can use the following command instead: 
```bash
curl https://packages.microsoft.com/keys/microsoft.asc | sudo tee /etc/apt/trusted.gpg.d/microsoft.asc
```


### 2. Manually download and register the SQL Server Ubuntu repository
```bash
curl -fsSL https://packages.microsoft.com/config/ubuntu/22.04/mssql-server-2022.list | sudo tee /etc/apt/sources.list.d/mssql-server-2022.list
```

### 3. Run the following commands to install SQL Server

```bash
sudo apt-get update
sudo apt-get install -y mssql-server
```


### 4. Run mssql-conf setup and follow the prompts to set the SA password and choose your edition
```bash
sudo /opt/mssql/bin/mssql-conf setup
```
