# IaaS

## Deploy K8s

```zsh
brew install ansible
ansible --version

git clone https://github.com/rihib/iaas.git
cd iaas

python3 -m venv kubespray-venv
source kubespray-venv/bin/activate
cd kubespray  # v2.24.1
pip install -U -r requirements.txt
cp -rfp ../iaas_sample inventory/iaas
# Update the `ansible.cfg`, `inventory/iaas/hosts.yml` files with your private key path and the IP addresses of your servers.

ssh-add YOUR_SSH_PRIVATE_KEY_PATH
ansible-playbook -i inventory/iaas/hosts.yml  --become --become-user=root playbooks/reset.yml
ansible-playbook -i inventory/iaas/hosts.yml  --become --become-user=root playbooks/cluster.yml
```
