# eap-access-logging-on-ocp

```
$ oc login ...
$ oc create -f https://raw.githubusercontent.com/jboss-container-images/jboss-eap-openshift-templates/eap74/eap74-openjdk11-image-stream.json

$ oc new-project eap-logging-demo
Now using project "eap-logging-demo" on server ...
$ oc project eap-logging-demo
$ oc new-app --template=eap74-basic-s2i \
 -p IMAGE_STREAM_NAMESPACE=eap-logging-demo \
 -p EAP_IMAGE_NAME=jboss-eap74-openjdk11-openshift:7.4.0 \
 -p EAP_RUNTIME_IMAGE_NAME=jboss-eap74-openjdk11-runtime-openshift:7.4.0 \
 -p SOURCE_REPOSITORY_URL=https://github.com/jboss-developer/jboss-eap-quickstarts \
 -p SOURCE_REPOSITORY_REF=7.4.x \
 -p GALLEON_PROVISION_LAYERS=jaxrs-server \
 -p CONTEXT_DIR=helloworld-html5
--> Deploying template "eap-logging-demo/eap74-basic-s2i" to project eap-logging-demo

     JBoss EAP 7.4.0
     ---------
     An example JBoss Enterprise Application Platform application. For more information about using this template, see https://github.com/jboss-container-images/jboss-eap-7-openshift-image/blob/eap74/README.adoc

     A new JBoss EAP based application has been created in your project.

     * With parameters:
        * Application Name=eap-app
        * EAP Image Name=jboss-eap74-openjdk11-openshift:7.4.0
        * EAP Runtime Image Name=jboss-eap74-openjdk11-runtime-openshift:7.4.0
        * Git Repository URL=https://github.com/jboss-developer/jboss-eap-quickstarts
        * Git Reference=7.4.x
        * Context Directory=helloworld-html5
        * Galleon layers=jaxrs-server
        * Enable ExampleDS datasource=false
        * Queues=
        * Topics=
        * AMQ cluster password=liIFIW7Q # generated
        * Github Webhook Secret=5aEGeLJh # generated
        * Generic Webhook Secret=Fh3ow4YW # generated
        * ImageStream Namespace=eap-logging-demo
        * JGroups Cluster Password=532IUKkL # generated
        * Deploy Exploded Archives=false
        * Maven mirror URL=
        * Maven Additional Arguments=-Dcom.redhat.xpaas.repo.jbossorg
        * ARTIFACT_DIR=
        * MEMORY_LIMIT=1Gi

--> Creating resources ...
    service "eap-app" created
    service "eap-app-ping" created
    route.route.openshift.io "eap-app" created
    imagestream.image.openshift.io "eap-app" created
    imagestream.image.openshift.io "eap-app-build-artifacts" created
    buildconfig.build.openshift.io "eap-app-build-artifacts" created
    buildconfig.build.openshift.io "eap-app" created
Warning: apps.openshift.io/v1 DeploymentConfig is deprecated in v4.14+, unavailable in v4.10000+
    deploymentconfig.apps.openshift.io "eap-app" created
--> Success
    Access your application via route 'eap-app-eap-logging-demo.apps.cluster-slhc7.slhc7.sandbox3037.opentlc.com' 
    Build scheduled, use 'oc logs -f buildconfig/eap-app-build-artifacts' to track its progress.
    Build scheduled, use 'oc logs -f buildconfig/eap-app' to track its progress.
    Run 'oc status' to view your app.
kfrankli@fedora:~$ oc get po

```

https://docs.redhat.com/en/documentation/red_hat_jboss_enterprise_application_platform/7.4/html-single/getting_started_with_jboss_eap_for_openshift_container_platform/index#deploy_eap_s2i
