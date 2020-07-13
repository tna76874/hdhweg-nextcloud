# homecloud-playbook

### Aim

nextcloud snap ubuntu server install

### Requirements

* A (virtual) server hosted by the company of your choice.
* A domain with an A-record pointing to the static IP-adress of your server.

### Prepare

Update your fresh VM and install git and ansible.

```
wget -qO setup.sh https://raw.githubusercontent.com/tna76874/hhdhweg-nextcloud/master/setup.sh && chmod +x setup.sh && sudo bash setup.sh && rm setup.sh
```

Edit `vars.yml` , e.g. with nano. Save the file with ctrl+o and close with ctrl+x.

```
sudo nano vars.yml
```

**Remove the ssh-keys inside the file `vars.yml` to prevent ssh access of the listed users.**

> **put your public ssh key inside vars.yml and define your user.**

Set the variable `letsencrypt_email` to your mailadress. You don't want your students to have bad warning messages on your nice websites once your letsencrypt certificates expired.

Set `main_domain` to the domain that points at your VM.

### Run

Run the playbook to fully set up your server.

```
sudo ansible-playbook main.yml
```

Now you can login to your Nextcloud-Server: yourdomain.yxz with the credentials in your `vars.yml`. Get them by printing the contents to the console.

```
cat vars.yml
```

Further secure your server by switching off password ssh authentication. **Be sure, that you have ssh access with your private key, otherwise you will lock yourself out of your server.**

```
sudo ansible-playbook secure.yml
```

### Maintenance

The snap container with nextcloud will automatically update itself with the latest stable branch. All you have to do is being happy sometimes about the nice new things you discover while browsing your nextcloud :)