# install Graylog

install java
```
sudo apt install openjdk-17-jre -y
```
install graylog
```bash
wget https://packages.graylog2.org/repo/packages/graylog-5.2-repository_latest.deb
sudo dpkg -i graylog-5.2-repository_latest.deb
sudo apt update
sudo apt install graylog-server -y
```

set password
```
echo -n <yourpassword> | sha256sum
```

copy password, edit file *server.conf* and paste to *root_password_sha2 = <paste hash>*
```bash
sudo nano /etc/graylog/server/server.conf
# root_password_sha2 = <paste hash>
```

start and enable
```bash
sudo systemctl daemon-reexec
sudo systemctl start graylog-server
sudo systemctl enable graylog-server
```

access graylog
```
http://<your-ip>:9000
```# install Graylog

install java
```
sudo apt install openjdk-17-jre -y
```
install graylog
```bash
wget https://packages.graylog2.org/repo/packages/graylog-5.2-repository_latest.deb
sudo dpkg -i graylog-5.2-repository_latest.deb
sudo apt update
sudo apt install graylog-server -y
```

set password
```
echo -n <yourpassword> | sha256sum
```

copy password, edit file *server.conf* and paste to *root_password_sha2 = <paste hash>*
```bash
sudo nano /etc/graylog/server/server.conf
# root_password_sha2 = <paste hash>
```

start and enable
```bash
sudo systemctl daemon-reexec
sudo systemctl start graylog-server
sudo systemctl enable graylog-server
```

access graylog
```
http://<your-ip>:9000
```

# install mongodb

install package
```bash
sudo apt-get install gnupg curl
```

import GPG public key mongodb
```bash
curl -fsSL https://www.mongodb.org/static/pgp/server-8.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-8.0.gpg \
   --dearmor
```

create list file
```bash
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-8.0.gpg ] https://repo.mongodb.org/apt/ubuntu noble/mongodb-org/8.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-8.0.list
```

update package
```bash
sudo apt update
```

install mongodb
```bash
sudo apt-get install -y mongodb-org
```

# install grafana

install package
```
sudo apt-get install -y apt-transport-https software-properties-common wget
```

import gpg key
```bash
sudo mkdir -p /etc/apt/keyrings/
wget -q -O - https://apt.grafana.com/gpg.key | gpg --dearmor | sudo tee /etc/apt/keyrings/grafana.gpg > /dev/null
```

add repository stable
```bash
echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
```

update package
```bash
sudo apt update
```

install grafana oss
```bash
sudo apt install grafana
```

run grafana
```bash
sudo systemctl daemon-reload
sudo systemctl start grafana-server
```

enable grafana
```bash
sudo systemctl enable grafana-server.service
```

check status grafana
```
sudo systemctl status grafana-server
```

access grafana
```
http://<your-ip>:3000
```
