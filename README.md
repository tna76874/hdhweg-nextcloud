# homecloud-playbook

### Aim

nextcloud snap ubuntu server install

### Requirements

* A (virtual) server hosted by the company of your choice. The server should be located in germany!
* A domain with an A-record pointing to the static IP-adress of your server.

### Prepare

Update your fresh VM and install git and ansible.

```
$ sudo apt update && sudo apt install nano git ansible -y
```

Clone this repo and create the playbook-variable-file.
```
$ cp vars.yml.example vars.yml
```

**Remove the ssh-keys inside the file `vars.yml` to prevent ssh access of the listed users.**

Set the variable `letsencrypt_email` to your mailadress. You don't want your students to have bad warning messages on your nice websites once your letsencrypt certificates expired.

Set `main_domain` to the domain that points at your VM. Be sure, that the subdomains `chat`, `tafel`, `jitsi`, `cryptpad` and `mumble` also points to your VM.

### Run

Run the playbook to fully set up your server.

```
$ sudo ansible-playbook main.yml
```