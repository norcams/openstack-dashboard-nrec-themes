# Branding
NREC branding for the OpenStack Horizon dashboard

# Installation for RHEL-based OpenStack Horizon Dashboard

1. Copy the file in local_settings.d to

```/usr/share/openstack-dashboard/openstack_dashboard/local/local_settings.d/```

2. Copy the theme folder in themes to

```/usr/share/openstack-dashboard/openstack_dashboard/themes```

3. (Darkmode hack) Replace hardcoded white color for even numbered rows with $table-bg-accent

```sed -i -e 's/$table-bg-even: #ffffff;/$table-bg-even: $table-bg-accent !default;/g' /usr/share/openstack-dashboard/openstack_dashboard/static/dashboard/scss/_variables.scss```

A patch for this exists in <ansible repo>

```bash
loc=vagrant
ansible-playbook -e myhosts=${loc}-dashboard -e patchfile=../files/patches/dashboard/0004-nrec-themes.diff -e basedir=/usr/share/openstack-dashboard/openstack_dashboard/static/dashboard/scss lib/patch.yaml
```

4. Restart httpd

```systemctl restart httpd```
