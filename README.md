Experitest - Selenium Agent ansible role
=========

This role will install \ uninstall selenium agent for mac os hosts

Requirements
------------

This role assumes that you have java 8 installed on the instance
Supports mac os hosts only.

Role Variables
--------------

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| state | should the application be present or absent | present, absent | present | no |
| app_version | application version to install | string | 12.8.680 | no |
| server_port | port number for the server | number | 8080 | no |
| autologin_pass | password for auto login | strings |  | yes |
| extra_java_options | extand java options | array of strings | [] | no |
| installation_folder | the folder in which the applction will be installed | string | for mac: ~/SeleniumAgent <br> for windows: ~\\SeleniumAgent  | no |
| custom_download_url | custom url to download the installation from (exe or dmg format) | string |  | no |
| start_after_install | should application start after installation is completed | boolean | True | no |
| clear_temp_folder | remove temp folder after installation | boolean | False | no |
| clear_before_install | removing old installation before installing new version | boolean | False | no |
| is_restrictive | enable restrictive mode for selenium browsers | boolean | false | no |
| external_proxy | enable external proxy for selenium browsers | boolean | false | no |

Example Playbook
----------------

#### [see working example](/example)
