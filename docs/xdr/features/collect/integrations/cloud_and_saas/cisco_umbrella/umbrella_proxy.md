uuid: 5a8ef52f-d143-4735-8546-98539fc07725
name: Umbrella Proxy Logs
type: intake

## Overview
Cisco Umbrella offers flexible, cloud-delivered security. It combines multiple security functions into one solution, so that protection can be extended to devices, remote users, and distributed locations anywhere. CISCO Umbrella is a leading provider of network security and recursive DNS services.

{!_shared_content/operations_center/integrations/generated/5a8ef52f-d143-4735-8546-98539fc07725.md!}

## Configure

{!_shared_content/operations_center/integrations/cisco_umbrella_set_aws_forwarding.md!}

### Create a S3 Event notification


Use the [following guide](https://docs.aws.amazon.com/AmazonS3/latest/userguide/enable-event-notifications.html) to create S3 Event Notification.
Once created:

1. In the General configuration, type `dnslogs/` as the Prefix
2. Select the notification for object creation in the Event type section
3. As the destination, choose the SQS service
4. Select the queue you created in the previous section

### Create the intake

Go to the [intake page](https://app.sekoia.io/operations/intakes) and create a new intake from the format `Cisco Umbrella Proxy`.

### Pull events

To start to pull events, you have to: 

1. Go to the [playbook page](https://app.sekoia.io/operations/playbooks) and create a new playbook with the [AWS Fetch new logs on S3 connector](../../../../automate/library/aws.md#fetch-new-logs-on-s3)
2. Set up the module configuration with the [AWS Access Key](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html), the secret key and the region name. Set up the trigger configuration with the name of the SQS queue and the intake key, from the intake previously created
3. Start the playbook and enjoy your events


## Further Readings
- [CISCO Umbrella User Guide - Manage your logs](https://docs.umbrella.com/deployment-umbrella/docs/setting-up-an-amazon-s3-bucket)
