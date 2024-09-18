(c) Copyright 2024 NREC

# Branding
NREC branding for the OpenStack Horizon dashboard

# Installation for RHEL-based OpenStack Horizon Dashboard

1. Copy the file in local_settings.d to

```/usr/share/openstack-dashboard/openstack_dashboard/local/local_settings.d/```

2. Copy the theme folder in themes to

```/usr/share/openstack-dashboard/openstack_dashboard/themes```

3. (Darkmode hack) Replace hardcoded white color for even numbered rows with $table-bg-accent

```sed -i -e 's/$table-bg-even: #ffffff;/$table-bg-even: $table-bg-accent !default;/g' /usr/share/openstack-dashboard/openstack_dashboard/static/dashboard/scss/_variables.scss```

4. Restart httpd

```systemctl restart httpd```
