# accessing object via your own REST API
User accesses to object storage only via this application. 

### Restricting Access to Specific IP Addresses 
(https://docs.cloud.oracle.com/en-us/iaas/Content/Identity/Tasks/managingnetworksources.htm?Highlight=network%20source#acres)

I have created network source in IAM as onlymyip 

Add the following policy 

```sh
allow group mygroup to use object-family in tenancy where request.networkSource.name='onlymyip'
```

### How to access your object
Replace object/bucket name with your own 

```sh
http://localhost:9000/image?object=OBJECT_NAME&bucket=BUCKET_NAME
```

If this application is running in OCI compute, you can add NSG to only allow the specific IPs to access this application.
https://docs.cloud.oracle.com/en-us/iaas/Content/Network/Concepts/networksecuritygroups.htm


If you use request-par.py, it also access to object only from source IP you defined in network source. 
