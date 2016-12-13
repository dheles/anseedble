# anseedble

A starting point for Ansible projects. Includes Vagrantfile and scripts for setting up VMs for ansibilization.

## things done by default:

### sets up a login user
via the [login-user role](https://github.com/dheles/ansible-role-login-user)

#### creates the user

    login_user: "deploy"

#### gives it sudo

TODO: grant the power to change

#### creates and deploys ssh keys for the user on the server

    create_login_user_key:  true
    login_user_key:         "{{ project }}_{{ environ }}"
    login_user_passphrase:  "change me in the vault file for the environment"
    key_type:               "rsa"
    key_size:               4096

### creates an ssh config entry
looks like this:

    # BEGIN app.test.dev dev
    Host app.test.dev app
    Hostname app.test.dev
    User deploy
    IdentityFile ~/.ssh/anseedble_dev
    PreferredAuthentications publickey
    IdentitiesOnly yes
    StrictHostKeyChecking no
    UserKnownHostsFile=/dev/null
    # END app.test.dev dev

not what you want? np. just say nah:

    create_ssh_config_entry: no

### secures ssh

TODO: deets

## recommended
(but not required): vagrant hostsupdater plugin
https://github.com/cogitatio/vagrant-hostsupdater
