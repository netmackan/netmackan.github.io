---
layout: post
title:  "Using a custom trust store in Jitsi"
date:   2014-04-11 18:46:35
categories: jitsi
---

Sometimes you don't want to trust all the certification authority (CA) certificates available in the Java truststore in your XMPP application. It could also be that you want to trust a specific CA only for the XMPP application.

Currently Jitsi uses the default Java trust store (at least on Linux) but it is possible to change this by specifying your own.

 
1) Create the trust store
-------------------------

Using the Java keytool command a new keystore can be created and the CA certificates that we want to trust imported into it:

{% highlight bash %}
keytool -importcert -trustcacerts -keystore jitsi-trust.jks -file StartCom.pem -alias startcom
keytool -importcert -trustcacerts -keystore jitsi-trust.jks -file MyCustomCA.pem -alias mycustomca
{% endhighlight %}

The command can be repeated for all CA certificates to import.

 
2) Configure Jitsi to use the trust store
-----------------------------------------

Currently the custom trust store is configured by specifying some configuration properties.

Tools -> Options -> Advanced -> Property Editor

Click "I am aware of the risks".

Add the following properties:

{% highlight properties %}
net.java.sip.communicator.service.cert.truststore.type: JKS
net.java.sip.communicator.service.cert.truststore.file: /path/to/jitsi-trust.jks
net.java.sip.communicator.service.cert.truststore.password: the key store password
{% endhighlight %}

![Jitsi property editor][prop-editor]


[prop-editor]: {{site.baseurl}}/resources/jitsi-property-editor-trust_0_o.png
