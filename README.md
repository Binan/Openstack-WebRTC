- hh
# Openstack WebRTC Gateway Heat Template

These are Openstack Heat template files that can be used for WebRTC Gateway deployment in Openstack cloud. You need to make your gateway server pulls its configuration on boot using curl from the standard metadata service (URL: http://169.254.169.254/latest/meta-data/) and stores the configuration in its database.This is systemd oneshot script. Then the gateway service starts after the boot script.

The template creates autoscaling group with policies and alarms. DELETE action is deployed for clean shutdown so when the server is determined to be killed, it cleans itself and signal Heat on completion. The image is built with Heat agents using diskimage-builder.

To execute the template you need to have Heat client installed:

- Source your keystone RC file
- Assuming all template files in the same directory. Execute this :
      # heat stack-create $StackName -f MainTemplate.yaml -e environment.yaml
