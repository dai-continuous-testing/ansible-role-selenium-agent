Experitest - Selenium Agent ansible role
=========

This role will install \ uninstall selenium agent for windows. <br>
For mac, currently it only supports selenium agent upgrade.

Requirements
------------

Supports windows and mac os hosts only.

Role Variables
--------------

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| state | should the application be present or absent | present, absent | present | no |
| app_version | application version to install | string | 12.12.782 | no |
| server_port | port number for the server | number | 8080 | no |
| autologin_pass | password for auto login (required for windows) | strings |  | yes |
| extra_application_properties | additional props to be override in application.properties file | dict | {} | no |
| extra_logback_properties | additional props to be override in logback.properties file | dict | {} | no |
| extra_java_options | extand java options | array of strings | [] | no |
| installation_folder | the folder in which the applcation will be installed | string | for mac: ~/SeleniumAgent <br> for windows: ~\\SeleniumAgent  | no |
| custom_download_url | custom url to download the installation from (exe or dmg format) | string |  | no |
| custom_download_username | username to download from custom url on windows | string |  | no |
| custom_download_password | password to download from custom url on windows | string |  | no |
| reboot_after_install | should system reboot after installation is completed | boolean | True | no |
| start_after_install | should application start after installation is completed | boolean | True | no |
| clear_temp_folder | remove temp folder after installation | boolean | False | no |
| clear_before_install | removing old installation before installing new version | boolean | False | no |
| kill_notepad | kill notepad/notepadd++ apps on windows | boolean | False | no |
| is_restrictive | enable restrictive mode for selenium browsers | boolean | True | no |
| enable_tunneling | enable or disable selenium browsers proxy | boolean | True | no |
| use_external_proxy | enable external proxy for selenium browsers | boolean | False | no |
| external_proxy_host | when use_external_proxy is True, set proxy hostname or ip  | string |  | no |
| external_proxy_port | when use_external_proxy is True, set proxy port | number |  | no |
| external_proxy_user | when use_external_proxy is True, set proxy user | string |  | no |
| external_proxy_password | when use_external_proxy is True, set proxy password | string |  | no |

Example Playbook
----------------

#### [see working example](/example)

<br>

Known issues
------------

### mojave:

- For mojave after reboot of the first upgrade, during the user loading we need to allow the system event pop-up for selenium.sh script

### catalina:

- For catalina after first upgrade we need to allow the Java pop-up, and as well to go to 'Security & Privacy' and to allow Java in the following 3 places - screen recording, full disk access, accessibility (same as doing in first installation via Install4j)

### mac:

- make sure the deployment user should have sudo permissions with 'NOPASSWD: ALL' privileges.

### windows:

- After windows updates sometimes winrm service get stopped and reset, To fix winrm reset issues, run [ansible-role-winrm-startup](https://github.com/ExperitestOfficial/ansible-role-winrm-startup) role on all windows machines once.
- currently its causing error with parallel windows selenium deployment, recommended to run one at a time or add "serial: 1" flag in playbook to deploy multiple selenium windows.
