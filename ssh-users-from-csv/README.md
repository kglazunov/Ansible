**Create users from csv file via Ansible and add permissions to /etc/sudoers if needed and send email with credentials.**
**Once generated password will be applied on each host from csv and stored as plaintext in the credentials/$username$/sshpassword.txt**

**Examples from the users.csv:**
```
Host:email:username:use_sudo:sudo_to
well.sf.ca.uss:kmitnik@well.sf.ca.uss:dono:yes:hadoop
well.sf.ca.uss:kmitnik@well.sf.ca.uss:kmitnik:no:
well.sf.ca.uss:tshimomura@ucsd.eduu:tshimomura:yes:apache,tomcat
```

**Steps before run**

  0) Allow less security app in your google account: https://myaccount.google.com/u/1/lesssecureapps?rfn=27&rfnc=1&eid=-1151598352600325229&et=0&asae=2&pli=1
  1) Fill the csv file with fqdn hostname,email address,username and etc.
  2) Change email settings in the csv.j2.
  3) Ensure that you have configured MTA in your host where you'll run the playbook.

**Run playbook**

  `ansible-playbook prepare_vars.yml;ansible-playbook -Kk -u username parse.yml`
