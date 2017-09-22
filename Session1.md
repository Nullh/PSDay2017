# DevOps via the Helpdesk
## Stuart Moore 
[](stuart-moore.com)

Age old problem:
* Want to implement new techniques
* No buy in
* Can't see the point
* etc...

The problem contains the solution! If you fix the same problem twice, script it! If you do it more than 5 times, automate it!
You get buy in by freeing up times.
Make sure this is source controlled, tested, add telemetry + feedback, automate it and deliver value faster. That's Devops!

JEA - Just Enough Administration
Role based means of granting limited access to administrative functions.
Create endpoints that users connect to. Users can run commands as a virtual user with higher permissions.
Endpoints can limit the functionality a user can do.

It's not just for helpdesk! You can run as a less privileged user, perform admin tasks this way and it can log what you do.

### Constrained EndPoints
They're what PS Remoting connects to.
These can me constrained by various methods.

You start with 4 endpoints - `Get-PSSessionConfiguration`
See Stuart's GitHub for examples.
Each endpoint is constrained by permissions (who can access)
Also constrained by commands they can run. You can even configure an endpoint with no language, to not allow an interactive session.
You can also restrict which providers a user can access - so you can disallow the endpoint connecting to the directories on disk.

### Creating an Endpoint
Needs to be in a module structure, but a basic skeleton is enough.
Needs to be in a standard location.
Must contain a .pssc and 0 or more .psrc

### Configuration changes
For Session Configs you need to re-register for changes to take effect, then restart WinRM
For Role capabilities you just need to update the files and you're good. Worthwhile restarting WinRM, but not necessary

### Constraining the Session
Follow Stuart's example script.
Worth noting that the name of the .psrc file is the name of the role.
If you're running with restricted remote permissions you can't load dlls or namespaces. If you're writing your own commands you can automatically import your own command, but if you're using other runspaces then you need to get clever to make it work.
In the example Stuart grants an individual user the permissions to end and start services. Then filters the allowable services to just the bits service.
With this you can even force parameters to be used with functions.

Transcripts can be logged from these. Logs every command and function run on the endpoint.
You can even add prefixes to commands so that Stop-Service can be overidden to Stop-<name>Service so that the command can be run in a local session but affect the remote server implicitly