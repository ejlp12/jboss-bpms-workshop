Download file `jboss-bpmsuite-6.1.0.GA-supplementary-tools.zip`

Extract

```
________________________________________________________________________________
| ejlp12 @ ejlp-macbook:~/playground/jbpm-6.1-rest-standalone-client
| => cd /Servers/BPMS-6.1-NEW/kie-config-cli-dist/
________________________________________________________________________________
| ejlp12 @ ejlp-macbook:/Servers/BPMS-6.1-NEW/kie-config-cli-dist
| => ls -l
total 80
-rw-rw-r--    1 ejlp12  staff    70K Apr  3 04:13 kie-config-cli-6.2.0.Final-redhat-4.jar
-rwxrwxr-x    1 ejlp12  staff   526B Apr  3 04:13 kie-config-cli.bat
-rwxr-xr-x    1 ejlp12  staff   436B Apr  3 04:13 kie-config-cli.sh
drwxrwxr-x  169 ejlp12  staff   5.6K Jul  3 20:58 lib/
________________________________________________________________________________
| ejlp12 @ ejlp-macbook:/Servers/BPMS-6.1-NEW/kie-config-cli-dist
| => ./kie-config-cli.sh
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=128m; support was removed in 8.0
********************************************************

************* Welcome to Kie config CLI ****************

********************************************************

>>Please specify location of remote git system repository [ssh://localhost:8001/system]

>>Please enter username:
bpmsAdmin
>>Please enter password:

>>Please enter command (type help to see available commands):
help
Result:
****************** KIE CLI Help ************************
********************************************************
Available commands:
	 exit - publishes any work, cleans up temporary directories and quits this command line tool
	 discard - won't publishes local changes, cleans up temporary directories and quits this command line tool
	 help - prints this message
	 list-repo - list available repositories
	 list-org-units - list available organizational units
	 list-deployment - list available deployments
	 create-org-unit - creates new organizational unit
	 remove-org-unit - remove existing organizational unit
	 add-deployment - add new deployment unit
	 remove-deployment - remove existing deployment
	 create-repo - creates new git repository
	 remove-repo - remove existing repository from config only
	 add-repo-org-unit - add repository to the organizational unit
	 remove-repo-org-unit - remove repository from the organizational unit
	 add-role-repo - add role(s) to repository
	 remove-role-repo - remove role(s) from repository
	 add-role-org-unit - add role(s) to organizational unit
	 remove-role-org-unit - remove role(s) from organizational unit
	 add-role-project - add role(s) to project
	 remove-role-project - remove role(s) from project
	 push-changes - pushes changes to upstream repository (only online mode)
	 fetch-changes - fetches changes from upstream repository (only online mode)
>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>Please enter command (type help to see available commands):

```

Coba paling tidak perintah berikut

  ```
	 list-repo 
	 list-org-units 
	 list-deployment 
	 exit
	```
