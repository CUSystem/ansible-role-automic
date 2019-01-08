# UC4/Automic Configuration 

Ansible role that installs UC4/Automic on RedHat 7

## Requirements

None.


## Dependencies

None.

## Notes

This role configures UC4 Unix service manager and agent.  It pulls the binaries down from a repository, such as Artifactory.

The UC4 user (default uc4) that is created uses both a password and uploads a public key.

For encrypting the password, see : https://docs.ansible.com/ansible/latest/reference_appendices/faq.html#how-do-i-generate-crypted-passwords-for-the-user-module

For example:

ansible all -i localhost, -m debug -a "msg={{ 'mypassword' | password_hash('sha512', 'mysecretsalt') }}"

And set the output to the encrypted_uc4_user_pass variable


## Variables

### Example of the minimum variables to set are:

encrypted_uc4_user_pass: <encrypted password>
  
uc4_rsapub: ssh-rsa AAAJFDSASDLKJF......

servicemanager_archive_location: "<path_to_servicemanage_archive>"

agent_archive_location: "<url_to_agent_archive>"

automic_ae_server_host:	"my.host.com"

automic_ae_server_port:	2217

### Common defaults that you may wish to override:

  licence_class: 'V' #[sic]
  automic_runtime_user_name: 'uc4'

  automic_runtime_group_name: 'uc4'

  automic_runtime_user_id: '601'

  automic_runtime_group_id: '601'

  automic_name: 'UC4'

  automic_system_name: 'UC4'

## License

MIT / BSD

## Maintainer Information
University of Colorado
joel.shure@cu.edu




