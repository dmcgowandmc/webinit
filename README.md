** webinit

* Description

The webinit ansible scripts are a set of bootstrap scripts which will initialize an ec2 on start up. It will perform the following

1. Install Apache / PHP and any other supporting packages
2. Download and install cloudwatch agent
3. Download and configure the CMS package (currently only wordpress supported)
4. Mount the EFS
5. Configure and enable the CMS package on apache

* Usage

The webinit ansible scripts are intended to be triggered by cloud-init on ec2 startup. All required parameters are provided by the cloud formation templates which spin up the underlying infrastructure.

If however you do want to run the scripts manually for debugging purposes, see command below.

ansible-playbook -i inventory/webstack init-webstack.yml --extra-vars "mywordpresssite_s3_utilities=<s3_bucket> mywordpresssite_db_wp_username=<wp_db_username> mywordpresssite_db_wp_password=<wp_db_password> mywordpresssite_db_wp_name=<wp_db_name> mywordpresssite_db_url=<db_instance_url> mywordpresssite_db_admin_username=<db_instance_username> mywordpresssite_db_admin_password=<db_instance_password> mywordpresssite_email_admin=<admin_email> mywordpresssite_fqdn=<fqdn>"