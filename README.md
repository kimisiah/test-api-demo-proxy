## DISCLAIMER: This repository is for demo purpose only and is not for commercial use.

## Getting Started
- [Download and install Maven 3.*](http://maven.apache.org/download.cgi)
- Clone this repo https://github.com/kimisiah/test-api-demo-proxy.git
- For API Proxy - ```cd src/api/api-demo/apiproxy```
- Execute ```mvn install -Ptest -Dusername={apigee-edge-email} -Dpassword={apigee-edge-password} -Dorg={apigee-edge-org} -Dapigee.hosturl={your-api-host-url}```

That's it! If everything ran smooth, you will see BUILD SUCCESS message at the of the execution of this command...

## Basic Commands – apigee.options

### Configure, package, import, deploy, and test bundle (default validate apigee.option) – Creates new revision

```mvn install -Ptest -Dusername=$ae_username -Dpassword=$ae_password -Dorg=testmyapi -Dapigee.hosturl=$ae_hosturl```

### Configure, package, import, override, deploy, and test bundle (default validate apigee.option) – Overrides current revision

```mvn install -Ptest -Dusername=$ae_username -Dpassword=$ae_password  -Dapigee.hosturl=$ae_hosturl -Doptions=validate,update```

### Undeploy and delete revision in the environment

```mvn install -Ptest -Dusername=$ae_username -Dpassword=$ae_password  -Dapigee.hosturl=$ae_hosturl -Doptions=clean```

### Configure and package bundle. Does not import

```mvn package -Ptest -Dusername=$ae_username -Dpassword=$ae_password  -Dapigee.hosturl=$ae_hosturl -Dorg=testmyapi```

### The following are available options:
a. clean - This will delete the last deployed revision in an environment.

b. validate - This will validate a bundle before importing. Thus if you want strict validation then its required.

c. inactive - This will just import the bundle without activating the bundle.

d. override - This is used for seamless deployment. This must be supplied with apigee.override.delay parameter. The apigee.override.delay expects delay to be given in seconds.

e. update - It will update the deployed revision .  This is similar to import with validation but no new revision is created. If there any errors in the bundle, error is thrown and the existing bundle is left intact. In case the revision they are trying to update is deployed, it will internally trigger undeployment and deployment. It is completely in the background and not visible in the response. It is advised not to update the deployed revision. (UI could show a warning or something in this case).
