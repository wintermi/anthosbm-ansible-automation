# Example Ansible Automation for Installing Anthos Bare Metal


## Setup Remote User
Make sure that the remote user account is configured to allow for the execution of sudo without the need to enter a password.  An example of how this can be achieved can be found below:

```
# Setup sudoers for remote user account e.g "ansible-runner"
sudo rm -f /etc/sudoers.d/*
cat <<EOF | sudo tee /etc/sudoers.d/00-ansible-runner
ansible-runner   ALL=(ALL) NOPASSWD:ALL
EOF
```

## Ansible Control Machine Setup
On your Ansible Control Machine, ensure that you install and initialize the Google Cloud SDK using these [instructions](https://cloud.google.com/sdk/docs). This process will install gcloud and gsutil.

Next we need to loging in with your Google Account which will be used by Ansible to manage the services and service accounts:
```
gcloud auth login --update-adc
```
and finally ensure that you setup the default Google Cloud Project
```
gcloud config set project "PROJECT_ID"
```
