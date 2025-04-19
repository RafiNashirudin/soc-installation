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
