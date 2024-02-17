# Install and Configure GitLab on Ubuntu

# **1.Install and configure the necessary dependencies**

```bash
sudo apt-get update
sudo apt-get install -y curl openssh-server ca-certificates postfix tzdata perl
```

# **2. Add the GitLab package repository and install the package**

```bash
curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash
```

# 3.Next,download and install the GitLab package

```bash
wget https://image.sudoix.ir/gitlab-ce_16.2.3-ce.0_amd64.deb
sudo dpkg -i gitlab-ce_16.2.3-ce.0_amd64.deb
```

# 4.Make sure you have correctly [set up your DNS](https://docs.gitlab.com/omnibus/settings/dns), and change https://gitlab.example.com to the URL at which you want to access your GitLab instance

- set Dns for url :

```bash
vim /etc/hosts
```

- set external url in gitlab.rb file :

```bash
vim /etc/gitlab/gitlab.rb

external_url 'http://192.168.31.132'
```

- next change external_url save gitlab.rb and run reconfigure command

```bash
gitlab-ctl reconfigure
```

# 5.check status firewall and allow access

```bash
sudo ufw status
sudo ufw allow http
sudo ufw allow https
sudo ufw allow openSSH
```

- after reconfigre gitlab-ctl

# 6. **Browse to the hostname and login**

Unless you provided a custom password during installation, a password will be randomly generated and stored for 24 hours in /etc/gitlab/initial_root_password. Use this password with username root to login.