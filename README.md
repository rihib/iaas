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
# Update the `ansible.cfg` and `inventory/iaas/hosts.yml` files with your private key path and the IP addresses of your servers.
# Update the `inventory/iaas/group_vars/all/all.yml` and `inventory/iaas/group_vars/k8s_cluster/k8s-cluster.yml` files with your desired configuration.

ssh-add YOUR_SSH_PRIVATE_KEY_PATH
ansible-playbook -i inventory/iaas/hosts.yml  --become --become-user=root playbooks/reset.yml
ansible-playbook -i inventory/iaas/hosts.yml  --become --become-user=root playbooks/cluster.yml
```
