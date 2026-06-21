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

5. Save the password

Write the password to the vault password file:
```bash
echo -n "THE_VAULT_PASSWORD" > ansible/.ansible_vault_pass
chmod 600 ansible/.ansible_vault_pass
```

6. Run the playbook from the ansible directory.

```bash
ansible-playbook main.yml
```
