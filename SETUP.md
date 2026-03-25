# 1. Create the ansible user
sudo useradd -m -s /bin/bash ansible

# 2. Set up SSH key auth
sudo mkdir -p /home/ansible/.ssh
sudo cp ~/.ssh/authorized_keys /home/ansible/.ssh/authorized_keys  # or paste your public key
sudo chown -R ansible:ansible /home/ansible/.ssh
sudo chmod 700 /home/ansible/.ssh
sudo chmod 600 /home/ansible/.ssh/authorized_keys

# 3. Passwordless sudo
echo 'ansible ALL=(ALL) NOPASSWD:ALL' | sudo tee /etc/sudoers.d/ansible
sudo chmod 440 /etc/sudoers.d/ansible

# 4. Disable password login for this user
sudo passwd -l ansible
