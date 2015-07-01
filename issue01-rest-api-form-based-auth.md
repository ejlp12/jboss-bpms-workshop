
```
Exception in thread "main" org.kie.services.client.api.command.exception.RemoteCommunicationException: The remote server requires form-based authentication.
	at org.kie.services.client.api.command.AbstractRemoteCommandObject.executeRestCommand(AbstractRemoteCommandObject.java:415)
	at org.kie.services.client.api.command.AbstractRemoteCommandObject.execute(AbstractRemoteCommandObject.java:124)
	at org.jbpm.services.task.impl.command.CommandBasedTaskService.getTasksOwned(CommandBasedTaskService.java:194)
	at com.redhat.gss.Main.main(Main.java:45)
Caused by: org.jboss.resteasy.client.ClientResponseFailure: Unable to find a MessageBodyReader of content-type text/html;charset="utf-8" and type null
	at org.jboss.resteasy.client.core.BaseClientResponse.createResponseFailure(BaseClientResponse.java:523)
	at org.jboss.resteasy.client.core.BaseClientResponse.createResponseFailure(BaseClientResponse.java:514)
	at org.jboss.resteasy.client.core.BaseClientResponse.readFrom(BaseClientResponse.java:415)
	at org.jboss.resteasy.client.core.BaseClientResponse.getEntity(BaseClientResponse.java:377)
	at org.jboss.resteasy.client.core.BaseClientResponse.getEntity(BaseClientResponse.java:350)
	at org.jboss.resteasy.client.core.BaseClientResponse.getEntity(BaseClientResponse.java:344)
	at org.kie.services.client.api.command.AbstractRemoteCommandObject.executeRestCommand(AbstractRemoteCommandObject.java:410)
	... 3 more
	```
	
	Tambahkan `useFormBasedAuth(true)`
	
	```
			RemoteRestRuntimeEngineFactory factory = RemoteRestRuntimeEngineFactory.newBuilder()
				   .addDeploymentId(DEPLOYMENT_ID)
				   .addUrl(url)
				   .addUserName(USER)
				   .addPassword(PASSWORD)
				   .addTimeout(5)
				   .useFormBasedAuth(true)
				   .build();
	```
