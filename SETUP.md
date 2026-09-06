# Setup

1. Create the ansible user.

```bash
sudo useradd -m -s /bin/bash ansible
```

2. Set up SSH key auth.

```bash
sudo mkdir -p /home/ansible/.ssh
sudo cp ~/.ssh/authorized_keys /home/ansible/.ssh/authorized_keys # or paste your public key
sudo chown -R ansible:ansible /home/ansible/.ssh
sudo chmod 700 /home/ansible/.ssh
sudo chmod 600 /home/ansible/.ssh/authorized_keys
```

3. Set up passwordless sudo.

```bash
echo 'ansible ALL=(ALL) NOPASSWD:ALL' | sudo tee /etc/sudoers.d/ansible
sudo chmod 440 /etc/sudoers.d/ansible
```

4. Disable password login for this user.

```bash
sudo passwd -l ansible
```

5. Install the required Ansible collections (from the ansible directory).

```bash
ansible-galaxy collection install -r requirements.yml
```

6. Create the inventory and variables from the examples, then edit both (replace every `CHANGE_ME`).

```bash
cp inventory/hosts.yml.example inventory/hosts.yml
cp group_vars/all/main.yml.example group_vars/all/main.yml
```

7. Run the playbook from the ansible directory.

```bash
ansible-playbook main.yml
```
