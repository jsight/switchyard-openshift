SwitchYard on OpenShift Express
===============================

This template helps you get up and running quickly with a SwitchYard application on
OpenShift Express.

Create an account at http://openshift.redhat.com/

Create a jbossas-7 application

    rhc app create -a swyesb -t jbosseap-6.0

Add the switchyard cartride

    rhc cartridge add switchyard-0.6

Add this upstream SwitchYard repo

    cd swyesb
    git remote add upstream -m master git://github.com/eschabell/switchyard-openshift.git
    git pull -s recursive -X theirs upstream master

Then push the repo to origin

    git push

That's it, you can now checkout your application at:

    http://swyesb-$yourdomain.rhcloud.com

Samples deployed with your application
--------------------------------------

This repository will deploy a sample called switchyard-quickstart-demo-orders.war. You can
play with the web interface to the OrderService:
    http://swyesb-$yourdomain.rhcloud.com/switchyard-quickstart-demo-orders/home.jsf

You can submit orders such as shown below in the SOAP message.

OpenShift does not allow external connections the range of ports it exposes: 15000 - 35530, 
these can only be accessed via the internal IP of our instance.

The internal access is done via the internal IP at:

    http://swyesb-$yourdomain.rhcloud.com:18001/demo-orders/OrderService?wsdl

A valid SOAP request is shown here:

    <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
       xmlns:urn="urn:switchyard-quickstart:bean-service:1.0">
       <soapenv:Header/>
       <soapenv:Body>
          <urn:submitOrder>
             <order>
                <orderId>1</orderId>
                <itemId>BUTTER</itemId>
                <quantity>20</quantity>
             </order>
          </urn:submitOrder>
       </soapenv:Body>
    </soapenv:Envelope>

Read more at the cloud link of your application from here, once it is deployed.

    http://swyesb-$yourdomain.rhcloud.com
