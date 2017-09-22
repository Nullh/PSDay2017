# Talking REST API & JSON with Powershell
## Esther Barthel 

### REST APIs and nitro
Based on client/server architecture.
Standards based platform independent way to communicate between client and server.
Runs on top of HHTP.
Easy to use when firewalls are in place (port 80 or 443)

NITRO is the name for the REST API service on the Citrix NetScaler which we're looking at as an example.

As a client we will use cURL or Postman for Chrome. INSTEAD we're going to use Powershell.

Always find the JSON documentation for the API you're communicating with! You need to know what operations you can perform and what syntax to user. The docs should tell you this.

### RESTFul APIs
We communicate with the API via a series of HTTP calls:
* VERB (GET, POST, PUT, DELETE)
* URI (http(s)://<ipaddress>/<whatever>/nsfeature?action=enable)
* HTTP  ()
* Request Header (Content-Type. Usually JSON. "content-type: application/json")
* Request Body (The JSON!)

### Invoke-RestMethod
It's time to run a script.
`Invoke-RestMethod` allows us to send the payload we constructed.
`Invoke-RestMethod -Method Post -URI $url -Body $JSONPayload -ContentType "application/json" -WebSession $SessionVar`

Pipe your pseudo JSON to ConvertTo-JSON, and don't forget the -Depth parm if your JSON is more than 2 deep!
