
# DANJR Deployment with Ansible

## Setup:

This assumes Windows/WSL:

```
wsl --install
wsl
sudo apt update
sudo apt install ansible -y
ansible --version
```

On EC2, create an Ubuntu instance with about 16GB storage. Make sure SSH and HTTP are allowed.

Generate an RSA pem key pair when doing so, save the key it offers you, and then move it to a place in WSL that you can access it later:

```
cp /mnt/c/Users/....../danjr.pem ~/
chmod 400 ~/danjr.pem
```

Enter this danjr-deploy folder within the WSL environment (will require replacing some of the code below with your own directory route):

```
cd /mnt/c/Users/....../danjr/danjr-deploy/
ansible -i inventory.ini danjr -m ping
```

Build and Deploy to AWS:
```
npm run build
ansible-playbook -i inventory.ini deploy.yml
```


## SSH into AWS EC2 Ubuntu Instance:

```
ssh -i ~/danjr-key.pem ubuntu@ec2-3-143-205-139.us-east-2.compute.amazonaws.com
```

