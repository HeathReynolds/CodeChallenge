
default.json is provided as an example of a working .json file that defines single tier hadoop cluster with HDFS being run localy (nodes are both data and compute). The only variables that need to be passed through from end user input to leverage default.json are the cluster name and the node quantites.
 

Serengetit REST Documentation - http://xxx.xxx.xxx.xxx:8080/restschema/service?APPLICATION=BigDataExtensions

Serengeti API - https://xxx.xxx.xxx.xxx:8443/serengeti/api

Serengeti API leverages cookies for auth, example : 

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


