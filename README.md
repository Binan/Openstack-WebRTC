# Openstack WebRTC Gateway Heat Template

These are Openstack Heat template files used for WebRTC Gateway deployment in Openstack cloud
Assuming the Gateway server pulls its configuration on boot (systemd oneshot script) and stores the configuration in its database. then it starts the gateway service.

This template creates autoscaling group with policies and alarms. DELETE action is deployed for clean shutdown so when the server is determined to be killed, it cleans itself and signal Heat (Heat Software Deployment resource types in the template). The image is built with Heat agents using diskimage-builder.

To execute the template you need to have Heat client installed:
1- source your keystone RC file
2- Assuming all template files in the same directory. Execute this :
 # heat stack-create Stack-01 -f MainTemplate.yaml -e environment.yaml
