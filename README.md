# AnsiblePlaybook
 Managing SSH keys and ensuring secure communication between servers.
 
# Prerequisites:
Ensure Ansible is installed on your control machine.
Create an external_vars file with relevant variables (e.g., external_vars.yml).
Run the Playbook:
Execute the playbook using the following command:
ansible-playbook -i inventory.ini playbook.yml

Replace inventory.ini with your actual inventory file.

# What the playbook does:

Receiving SSH Host Keys:
Connects to all hosts (specified by hosts: all).
Disables gathering facts until after the host key has been accepted.
Reads variables from an external file (vars_files: external_vars).
Checks if the SSH host key for “worker03” exists. If not, scans and appends it to the known_hosts file.
Gathering Facts:
Focuses on the “worker03” host.
Gathers system facts using the setup module.
Adding an SSH Authorized Key:
Switches focus to the “worker03” host.
Reads variables from the same external file (vars_files: external_vars).
Ensures that an SSH key (presumably the public key from /home/ansible/.ssh/id_rsa.pub) is authorized for the user “ansible” on the “worker03” host.
