# Impact UI show blank screen after upgrade Impact Fix Pack
* Reference: http://www-01.ibm.com/support/docview.wss?uid=swg22000341
* Verify Impact admin view status: https://IMPACTHOST:16311/impactAdmin/jsp/impactAdminView.jsp
* Verify Impact admin console deployment status: https://IMPACTHOST:16311/ibm/console/rest/deployments/details
* Output should contains at least 1 deployment
* If output does not contain deployment, redeploy Impact admin console
```bash
# $IMPACT_HOME/sdk/bin/java -jar $IMPACT_HOME/cli/cli.jar -deployUrl /impactAdmin/jsp/impactAdminDeploy.jsp -consoleRest https://localhost:16311/ibm/console/rest -deployNotificationUrl https://localhost:16311/impactAdmin/NCLogoutServlet -username ADMIN -password PASSWORD 
```
* Deployment may error due to SSL/TLS version, enable TLSv1.2 then restart Impact server and redeploy again
```bash
# vi /opt/IBM/tivoli/impact71/wlp/usr/servers/ImpactUI/server.xml
<ssl id="defaultSSLConfig" keyStoreRef="defaultKeyStore" trustStoreRef="defaultTrustStore" sslProtocol="TLSv1.2" securityLevel="CUSTOM" enabledCiphers="TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA TLS_RSA_WITH_AES_128_CBC_SHA"/>
# $IMPACT_HOME/bin/stopGUIServer.sh
# $IMPACT_HOME/bin/startGUIServer.sh
