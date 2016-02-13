# CodeChallenge
For our first unofficial EMC CodeChallenge (details on #EMC on CodeCommunity slack, EMC/VCE only) we are working with VMware Big Data Extensions and the Serengeti API. Big Data Extensions is a cluster management layer that orcestrates the creation of Hadoop clousters. Our goal is to pass a json file to the serengeti API, with specific fields being inputed by the end user as part of a request. 

default.json is provided as an example of a working .json file that defines single tier hadoop cluster with HDFS being run localy (nodes are both data and compute). The only variables that need to be passed through from end user input to leverage default.json are the cluster name and the node quantites.

compute.json will be provided soon. Compute.json is a working example that defines a compute only hadoop cluster, HDFS runs remotly and nodes are compute only. Variables that need to be passed through from end user input to leverage compute.json are the cluster name, node quantities, and an HDFS location. 

Accessing the lab enviroment : 
There is a lab with BDE running inside the EMC network 

Serengetit REST Documentation - http://10.25.90.124:8080/restschema/service?APPLICATION=BigDataExtensions

Serengeti API - https://10.25.90.124:8443/serengeti/api

Serengeti API leverages cookies for auth, example (user/pass in private slack, email me to be added) : 

curl -c cookies.txt -i -k -d 'j_username=******@vsphere.local&j_password=******' -X POST https://10.25.90.124:8443/serengeti/j_spring_security_check

HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Set-Cookie: JSESSIONID=227537474CEF0143C1BD3C922F5D8838; Path=/serengeti; Secure
Content-Length: 0
Date: Fri, 12 Feb 2016 13:22:39 GMT

Example of creating a cluster with a REST call, and succesful response : 

curl -i -H "Content-type:application/json" -3 -b cookies.txt -X POST -d @default.json https://10.25.90.124:8443/serengeti/api/clusters --insecure --digest

[9:37] 
HTTP/1.1 100 Continue

HTTP/1.1 202 Accepted
Server: Apache-Coyote/1.1
Location: https://10.25.90.124:8443/serengeti/api/task/180
Content-Length: 0
Date: Fri, 12 Feb 2016 15:34:33 GMT


