# Launching a webserver on AWS using Cloudformation

This cloudformation stack launches the following resources: 

- An instance with webserver configured 
- An Application Load Balancer 
- An Alarm for Application Load Balancer to monitor and ensure the service is always up and running.

### To launch : 

To launch the stack, you must have aws cli configured. 

The parameters that need to be configured for the stack are configured in the `parameters.json` file. Two Public subnets are needed for the Application Load balancer and one private subnet needs to be specified for the webserver instance. You will also need a keypair specified as a parameter to be able to ssh into your webserver if needed. Configure accordingly. 

Then, run the following command : 

```
aws cloudformation create-stack --stack-name webserver --template-body file://webserver.yaml --parameters file://parameters.json

```

To get the output of the cloudformation stack which contains the DNS name for the application loadbalancer, run the following command: 

``` 
aws cloudformation describe-stacks --stack-name webserver 
``` 

Then go to the loadbalancer's DNS name in a browser and voila! 
