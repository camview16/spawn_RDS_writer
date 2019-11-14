# Spawn AWS RDS writer

This script should be used as a cronjob.
The two internal scripts of this code repository will eventually do two things, one will check for the ALARM trigger from the Cloudwatch alarm. This needs to be set on the AWS RDS writer monitoring as required. Once this trigger is detected it will call the script which will up scale the writer instance and temporarilly stop the current script till the entire upgrading process. Also fail over process has been setup which would re assign the old writer instance as the new writer after the upgrade process if at all the reader has been promoted as a new writer.

Schedule the cron as follows :
* * * * * /bin/sh check_RDS_metric_status >> /home/ubuntu/logs/spawn_RDS.log 2>&1 &
