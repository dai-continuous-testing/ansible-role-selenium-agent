
# Example usage

to use the example:
- cd into the example folder

- install dependencies \
  *ansible-galaxy install -r requirements.yml*

- run the playbook \
  *ansible-playbook site.yml -i inventory.ini -k --ask-sudo-pass*

- put the admin password and confirm

## Known issues

## mac runner
when running ansible scripts from mac to winrm.\
actions are required:
- pip install "pywinrm>=0.2.2"
- *export OBJC_DISABLE_INITIALIZE_FORK_SAFETY=YES*

## mac target
Only supports selenium upgrades.


### make sure to add:
    export PATH="/usr/local/bin:$PATH" >> ~/.bashrc

### mojave:

For mojave after reboot of the first upgrade, during the user loading we need to allow the system event pop-up for selenium.sh script

### catalina:

For catalina after first upgrade we need to allow the Java pop-up, and as well to go to 'Security & Privacy' and to allow Java in the following 3 places - screen recording, full disk access, accessibility (same as doing in first installation via Install4j)

## windows target
run the bootstrap.ps1 script in the target machine\
NOTE:\
*update username and password first*

### After windows updates sometimes winrm service get stopped and reset, To fix winrm reset issues

- run [ansible-role-winrm-startup](https://github.com/ExperitestOfficial/ansible-role-winrm-startup) role on all windows machines once.
