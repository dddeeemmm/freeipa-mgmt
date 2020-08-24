freeipa-mgmt
=========

    Manage Free IPA entities and content: users, dns zones, groups, hbac, sudo
    Create user password and send template email

Requirements
------------

    User with Enroll Permitions

Role Variables
--------------

    ipa_mode:                       [required] users | groups | dns | hbac | sudo 
    ipa_domain:                     [required] domain name
    ipa_host:                       [default: ipa_servers | random ] host where command will be executed
    ipa_servers:                    [required] list of ipa server hosts
    ipa_validate_certs:             [default: false] validate certs before execute commands
    ipa_username:                   [not required] will be requested interactively
    ipa_password:                   [not required] will be requested interactively
    
    ipa_user_state:                 [default: present] present | absent
    ipa_user_pwd:                   [default: ipa_random if item.state == 'present' else ''] user password
    ipa_user_upd_pwd:               [default: 'always' if item.state == 'present' else 'on_create'] user update password policy
    ipa_user_name:                  [default: item.uid] user name
    ipa_user_sn:                    [default: item.uid] user sername
    ipa_user_mail:                  [default: item.uid@ipa_mail_domain] user email
    ipa_user_phone:                 [default: ''] user phone
    ipa_user_ssh:                   [default: ''] user ssh public key
    
    ipa_group_state:                [default: present] group state
    
    ipa_dnszone_state:              [default: present] dns zone state
    ipa_dnszone_dynamicupdate:      [default: true] dns zone dynamic update state
    
    ipa_mail_send:                  [default: true] send user email after change password
    ipa_mail_domain:                [required] user mail domain
    ipa_mail_host:                  [required] send mail host
    ipa_mail_port:                  [required] send mail port
    ipa_mail_secure:                [required] always | never | starttls | try
    ipa_mail_username:              [required] send mail username
    ipa_mail_password:              [required] send mail password
    ipa_mail_from:                  [required] send mail from
    ipa_mail_charset:               [required] send mail charset
    ipa_mail_subtype:               [required] html | plain
    ipa_mail_subject:               [required] send mail subject
    ipa_mail_body:                  [required] send mail body
    
Example Playbook
----------------
    
    - hosts: localhost
      roles:
        - { name: freeipa-mgmt, tags: im }

Example Run
----------------

    ansible-playbook freeipa-mgmt.yml

License
-------

    MIT

Author Information
------------------

    Dmitrij Petrov
