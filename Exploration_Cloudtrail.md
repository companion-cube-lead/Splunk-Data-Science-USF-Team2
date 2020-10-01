``` r
library(data.table)
library(lubridate)
```

    ## Warning: package 'lubridate' was built under R version 3.6.3

    ## 
    ## Attaching package: 'lubridate'

    ## The following objects are masked from 'package:data.table':
    ## 
    ##     hour, isoweek, mday, minute, month, quarter, second, wday, week,
    ##     yday, year

    ## The following objects are masked from 'package:base':
    ## 
    ##     date, intersect, setdiff, union

``` r
library(ggplot2)
```

    ## Warning: package 'ggplot2' was built under R version 3.6.3

``` r
cloudtrail <- fread("dataset.csv")
```

``` r
cloudtrail[, .N, by = errorCode]
```

    ##                                 errorCode    N
    ##  1:                               success 4410
    ##  2:               NoSuchCORSConfiguration  149
    ##  3:                          NoSuchTagSet   55
    ##  4:          NoSuchLifecycleConfiguration  145
    ##  5:                 NoSuchEntityException   11
    ##  6:                    NoSuchBucketPolicy   49
    ##  7:            NoSuchWebsiteConfiguration    1
    ##  8: ReplicationConfigurationNotFoundError    1
    ##  9:          Client.InstanceLimitExceeded  280
    ## 10:          Client.UnauthorizedOperation  231
    ## 11:                    Client.Unsupported  104
    ## 12:                          AccessDenied    7
    ## 13:   Server.InsufficientInstanceCapacity    7

``` r
cloudtrail[errorCode == 'Client.InstanceLimitExceeded']
```

    ##                                                 _bkt         _cd
    ##   1: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:2456239
    ##   2: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:2456191
    ##   3: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:2456143
    ##   4: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:2456030
    ##   5: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:2455982
    ##  ---                                                            
    ## 276: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:3166026
    ## 277: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:3165978
    ## 278: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:3006968
    ## 279: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:3006830
    ## 280: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:3006782
    ##      _eventtype_color _indextime
    ##   1:             none 1534757276
    ##   2:             none 1534757276
    ##   3:             none 1534757276
    ##   4:             none 1534757276
    ##   5:             none 1534757276
    ##  ---                            
    ## 276:             none 1534757708
    ## 277:             none 1534757708
    ## 278:             none 1534757621
    ## 279:             none 1534757621
    ## 280:             none 1534757621
    ##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         _raw
    ##   1:      {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:20:58Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.InstanceLimitExceeded"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-4d46d534"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""x1e.8xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""248c07e6-825c-4716-b464-a3334282c8a4"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit."", ""eventName"": ""RunInstances"", ""requestID"": ""5fe1721a-4312-431b-86a5-90f74ec6bd3e"", ""awsRegion"": ""eu-west-1""}
    ##   2:       {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:21:05Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.InstanceLimitExceeded"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-4d46d534"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""h1.4xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""fc655d96-7d57-4362-a42b-b8a03162628a"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit."", ""eventName"": ""RunInstances"", ""requestID"": ""2e6622b2-1f17-4b84-9602-0a50614ad4a5"", ""awsRegion"": ""eu-west-1""}
    ##   3:     {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:20:31Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.InstanceLimitExceeded"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-4d46d534"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""x1e.32xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""0fec3685-cc49-4672-a84e-703ce1a10c04"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit."", ""eventName"": ""RunInstances"", ""requestID"": ""d6359b89-ee16-45fa-9cc9-1a8bb8a460e7"", ""awsRegion"": ""eu-west-1""}
    ##   4:      {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:20:33Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.InstanceLimitExceeded"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-4d46d534"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""c5.18xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""efec939e-abdd-4c74-83cd-9cfba955c134"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit."", ""eventName"": ""RunInstances"", ""requestID"": ""cde55918-87e2-4dc4-abda-c748ce2a519b"", ""awsRegion"": ""eu-west-1""}
    ##   5:      {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:20:35Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.InstanceLimitExceeded"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-4d46d534"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""i3.16xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""6a3c04ec-37dd-45a5-badb-c52047b330ae"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit."", ""eventName"": ""RunInstances"", ""requestID"": ""3b882c64-2776-4e6a-85cf-560ef3b268af"", ""awsRegion"": ""eu-west-1""}
    ##  ---                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
    ## 276:  {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:18:38Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.InstanceLimitExceeded"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-67973709"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""c5.2xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""b772337c-bb7e-4bdc-9c4b-c8bd1701817f"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit."", ""eventName"": ""RunInstances"", ""requestID"": ""fe72256a-234f-4566-8c16-cdc2188af195"", ""awsRegion"": ""ap-northeast-2""}
    ## 277: {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:17:24Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.InstanceLimitExceeded"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-67973709"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""c5.18xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""fd689897-be2a-480d-b060-8bef7941ed93"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit."", ""eventName"": ""RunInstances"", ""requestID"": ""a42576ef-3adf-4dd5-a8c5-29da1bdb2621"", ""awsRegion"": ""ap-northeast-2""}
    ## 278:       {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:21:53Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.InstanceLimitExceeded"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-d7aab2b3"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""i3.8xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""6d25ba95-82ea-4b07-93fd-abc1b104dd35"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit."", ""eventName"": ""RunInstances"", ""requestID"": ""413965b3-6e9a-49bc-b19b-0e7aea5822f8"", ""awsRegion"": ""eu-west-2""}
    ## 279:      {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:21:34Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.InstanceLimitExceeded"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-d7aab2b3"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""r4.16xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""cdc70352-ce86-45c2-ae67-84f2d7bf8c2a"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit."", ""eventName"": ""RunInstances"", ""requestID"": ""7c6459eb-450e-4556-a9fc-3338fa5980de"", ""awsRegion"": ""eu-west-2""}
    ## 280:       {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:21:58Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.InstanceLimitExceeded"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-d7aab2b3"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""c5.4xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""62dccd77-6478-48ea-986f-80ea0502e7c2"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit."", ""eventName"": ""RunInstances"", ""requestID"": ""3ad1658e-75e0-43ce-978f-9a1b45f1cb12"", ""awsRegion"": ""eu-west-2""}
    ##         _sourcetype      _time  action additionalEventData.LoginTo
    ##   1: aws:cloudtrail 1534756858 created                            
    ##   2: aws:cloudtrail 1534756865 created                            
    ##   3: aws:cloudtrail 1534756831 created                            
    ##   4: aws:cloudtrail 1534756833 created                            
    ##   5: aws:cloudtrail 1534756835 created                            
    ##  ---                                                              
    ## 276: aws:cloudtrail 1534756718 created                            
    ## 277: aws:cloudtrail 1534756644 created                            
    ## 278: aws:cloudtrail 1534756913 created                            
    ## 279: aws:cloudtrail 1534756894 created                            
    ## 280: aws:cloudtrail 1534756918 created                            
    ##      additionalEventData.MFAUsed additionalEventData.MobileVersion
    ##   1:                                                              
    ##   2:                                                              
    ##   3:                                                              
    ##   4:                                                              
    ##   5:                                                              
    ##  ---                                                              
    ## 276:                                                              
    ## 277:                                                              
    ## 278:                                                              
    ## 279:                                                              
    ## 280:                                                              
    ##      additionalEventData.vpcEndpointId apiVersion               app
    ##   1:                                              ec2.amazonaws.com
    ##   2:                                              ec2.amazonaws.com
    ##   3:                                              ec2.amazonaws.com
    ##   4:                                              ec2.amazonaws.com
    ##   5:                                              ec2.amazonaws.com
    ##  ---                                                               
    ## 276:                                              ec2.amazonaws.com
    ## 277:                                              ec2.amazonaws.com
    ## 278:                                              ec2.amazonaws.com
    ## 279:                                              ec2.amazonaws.com
    ## 280:                                              ec2.amazonaws.com
    ##      authentication_method      awsRegion aws_account_id change_type
    ##   1:                            eu-west-1       6.23e+11         EC2
    ##   2:                            eu-west-1       6.23e+11         EC2
    ##   3:                            eu-west-1       6.23e+11         EC2
    ##   4:                            eu-west-1       6.23e+11         EC2
    ##   5:                            eu-west-1       6.23e+11         EC2
    ##  ---                                                                
    ## 276:                       ap-northeast-2       6.23e+11         EC2
    ## 277:                       ap-northeast-2       6.23e+11         EC2
    ## 278:                            eu-west-2       6.23e+11         EC2
    ## 279:                            eu-west-2       6.23e+11         EC2
    ## 280:                            eu-west-2       6.23e+11         EC2
    ##           command date_hour date_mday date_minute date_month date_second
    ##   1: RunInstances         9        20          27     august          56
    ##   2: RunInstances         9        20          27     august          56
    ##   3: RunInstances         9        20          27     august          56
    ##   4: RunInstances         9        20          27     august          56
    ##   5: RunInstances         9        20          27     august          56
    ##  ---                                                                    
    ## 276: RunInstances         9        20          35     august           8
    ## 277: RunInstances         9        20          35     august           8
    ## 278: RunInstances         9        20          33     august          41
    ## 279: RunInstances         9        20          33     august          41
    ## 280: RunInstances         9        20          33     august          41
    ##      date_wday date_year date_zone desc dest               dvc
    ##   1:    monday      2018         0           ec2.amazonaws.com
    ##   2:    monday      2018         0           ec2.amazonaws.com
    ##   3:    monday      2018         0           ec2.amazonaws.com
    ##   4:    monday      2018         0           ec2.amazonaws.com
    ##   5:    monday      2018         0           ec2.amazonaws.com
    ##  ---                                                          
    ## 276:    monday      2018         0           ec2.amazonaws.com
    ## 277:    monday      2018         0           ec2.amazonaws.com
    ## 278:    monday      2018         0           ec2.amazonaws.com
    ## 279:    monday      2018         0           ec2.amazonaws.com
    ## 280:    monday      2018         0           ec2.amazonaws.com
    ##                         errorCode
    ##   1: Client.InstanceLimitExceeded
    ##   2: Client.InstanceLimitExceeded
    ##   3: Client.InstanceLimitExceeded
    ##   4: Client.InstanceLimitExceeded
    ##   5: Client.InstanceLimitExceeded
    ##  ---                             
    ## 276: Client.InstanceLimitExceeded
    ## 277: Client.InstanceLimitExceeded
    ## 278: Client.InstanceLimitExceeded
    ## 279: Client.InstanceLimitExceeded
    ## 280: Client.InstanceLimitExceeded
    ##                                                                                                                                                                                                               errorMessage
    ##   1: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##   2: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##   3: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##   4: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##   5: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##  ---                                                                                                                                                                                                                      
    ## 276: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ## 277: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ## 278: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ## 279: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ## 280: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##                                   eventID    eventName       eventSource
    ##   1: 248c07e6-825c-4716-b464-a3334282c8a4 RunInstances ec2.amazonaws.com
    ##   2: fc655d96-7d57-4362-a42b-b8a03162628a RunInstances ec2.amazonaws.com
    ##   3: 0fec3685-cc49-4672-a84e-703ce1a10c04 RunInstances ec2.amazonaws.com
    ##   4: efec939e-abdd-4c74-83cd-9cfba955c134 RunInstances ec2.amazonaws.com
    ##   5: 6a3c04ec-37dd-45a5-badb-c52047b330ae RunInstances ec2.amazonaws.com
    ##  ---                                                                    
    ## 276: b772337c-bb7e-4bdc-9c4b-c8bd1701817f RunInstances ec2.amazonaws.com
    ## 277: fd689897-be2a-480d-b060-8bef7941ed93 RunInstances ec2.amazonaws.com
    ## 278: 6d25ba95-82ea-4b07-93fd-abc1b104dd35 RunInstances ec2.amazonaws.com
    ## 279: cdc70352-ce86-45c2-ae67-84f2d7bf8c2a RunInstances ec2.amazonaws.com
    ## 280: 62dccd77-6478-48ea-986f-80ea0502e7c2 RunInstances ec2.amazonaws.com
    ##                 eventTime  eventType eventVersion
    ##   1: 2018-08-20T09:20:58Z AwsApiCall         1.05
    ##   2: 2018-08-20T09:21:05Z AwsApiCall         1.05
    ##   3: 2018-08-20T09:20:31Z AwsApiCall         1.05
    ##   4: 2018-08-20T09:20:33Z AwsApiCall         1.05
    ##   5: 2018-08-20T09:20:35Z AwsApiCall         1.05
    ##  ---                                             
    ## 276: 2018-08-20T09:18:38Z AwsApiCall         1.05
    ## 277: 2018-08-20T09:17:24Z AwsApiCall         1.05
    ## 278: 2018-08-20T09:21:53Z AwsApiCall         1.05
    ## 279: 2018-08-20T09:21:34Z AwsApiCall         1.05
    ## 280: 2018-08-20T09:21:58Z AwsApiCall         1.05
    ##                                                                         eventtype
    ##   1: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors
    ##   2: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors
    ##   3: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors
    ##   4: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors
    ##   5: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors
    ##  ---                                                                             
    ## 276: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors
    ## 277: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors
    ## 278: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors
    ## 279: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors
    ## 280: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors
    ##                 host  index linecount                          msg object
    ##   1: splunk.froth.ly botsv3         1 Client.InstanceLimitExceeded       
    ##   2: splunk.froth.ly botsv3         1 Client.InstanceLimitExceeded       
    ##   3: splunk.froth.ly botsv3         1 Client.InstanceLimitExceeded       
    ##   4: splunk.froth.ly botsv3         1 Client.InstanceLimitExceeded       
    ##   5: splunk.froth.ly botsv3         1 Client.InstanceLimitExceeded       
    ##  ---                                                                     
    ## 276: splunk.froth.ly botsv3         1 Client.InstanceLimitExceeded       
    ## 277: splunk.froth.ly botsv3         1 Client.InstanceLimitExceeded       
    ## 278: splunk.froth.ly botsv3         1 Client.InstanceLimitExceeded       
    ## 279: splunk.froth.ly botsv3         1 Client.InstanceLimitExceeded       
    ## 280: splunk.froth.ly botsv3         1 Client.InstanceLimitExceeded       
    ##      object_category object_id    product
    ##   1:        instance           CloudTrail
    ##   2:        instance           CloudTrail
    ##   3:        instance           CloudTrail
    ##   4:        instance           CloudTrail
    ##   5:        instance           CloudTrail
    ##  ---                                     
    ## 276:        instance           CloudTrail
    ## 277:        instance           CloudTrail
    ## 278:        instance           CloudTrail
    ## 279:        instance           CloudTrail
    ## 280:        instance           CloudTrail
    ##                                                                punct readOnly
    ##   1: {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""       NA
    ##   2: {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""       NA
    ##   3: {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""       NA
    ##   4: {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""       NA
    ##   5: {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""       NA
    ##  ---                                                                         
    ## 276: {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""       NA
    ## 277: {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""       NA
    ## 278: {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""       NA
    ## 279: {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""       NA
    ## 280: {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""       NA
    ##                                                                                                                                                                                                                     reason
    ##   1: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##   2: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##   3: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##   4: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##   5: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##  ---                                                                                                                                                                                                                      
    ## 276: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ## 277: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ## 278: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ## 279: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ## 280: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##      recipientAccountId         region                            requestID
    ##   1:           6.23e+11      eu-west-1 5fe1721a-4312-431b-86a5-90f74ec6bd3e
    ##   2:           6.23e+11      eu-west-1 2e6622b2-1f17-4b84-9602-0a50614ad4a5
    ##   3:           6.23e+11      eu-west-1 d6359b89-ee16-45fa-9cc9-1a8bb8a460e7
    ##   4:           6.23e+11      eu-west-1 cde55918-87e2-4dc4-abda-c748ce2a519b
    ##   5:           6.23e+11      eu-west-1 3b882c64-2776-4e6a-85cf-560ef3b268af
    ##  ---                                                                       
    ## 276:           6.23e+11 ap-northeast-2 fe72256a-234f-4566-8c16-cdc2188af195
    ## 277:           6.23e+11 ap-northeast-2 a42576ef-3adf-4dd5-a8c5-29da1bdb2621
    ## 278:           6.23e+11      eu-west-2 413965b3-6e9a-49bc-b19b-0e7aea5822f8
    ## 279:           6.23e+11      eu-west-2 7c6459eb-450e-4556-a9fc-3338fa5980de
    ## 280:           6.23e+11      eu-west-2 3ad1658e-75e0-43ce-978f-9a1b45f1cb12
    ##      requestParameters
    ##   1:                  
    ##   2:                  
    ##   3:                  
    ##   4:                  
    ##   5:                  
    ##  ---                  
    ## 276:                  
    ## 277:                  
    ## 278:                  
    ## 279:                  
    ## 280:                  
    ##      requestParameters.AccessControlPolicy.AccessControlList.Grant{}.Grantee.DisplayName
    ##   1:                                                                                    
    ##   2:                                                                                    
    ##   3:                                                                                    
    ##   4:                                                                                    
    ##   5:                                                                                    
    ##  ---                                                                                    
    ## 276:                                                                                    
    ## 277:                                                                                    
    ## 278:                                                                                    
    ## 279:                                                                                    
    ## 280:                                                                                    
    ##      requestParameters.AccessControlPolicy.AccessControlList.Grant{}.Grantee.ID
    ##   1:                                                                           
    ##   2:                                                                           
    ##   3:                                                                           
    ##   4:                                                                           
    ##   5:                                                                           
    ##  ---                                                                           
    ## 276:                                                                           
    ## 277:                                                                           
    ## 278:                                                                           
    ## 279:                                                                           
    ## 280:                                                                           
    ##      requestParameters.AccessControlPolicy.AccessControlList.Grant{}.Grantee.URI
    ##   1:                                                                            
    ##   2:                                                                            
    ##   3:                                                                            
    ##   4:                                                                            
    ##   5:                                                                            
    ##  ---                                                                            
    ## 276:                                                                            
    ## 277:                                                                            
    ## 278:                                                                            
    ## 279:                                                                            
    ## 280:                                                                            
    ##      requestParameters.AccessControlPolicy.AccessControlList.Grant{}.Grantee.xmlns:xsi
    ##   1:                                                                                  
    ##   2:                                                                                  
    ##   3:                                                                                  
    ##   4:                                                                                  
    ##   5:                                                                                  
    ##  ---                                                                                  
    ## 276:                                                                                  
    ## 277:                                                                                  
    ## 278:                                                                                  
    ## 279:                                                                                  
    ## 280:                                                                                  
    ##      requestParameters.AccessControlPolicy.AccessControlList.Grant{}.Grantee.xsi:type
    ##   1:                                                                                 
    ##   2:                                                                                 
    ##   3:                                                                                 
    ##   4:                                                                                 
    ##   5:                                                                                 
    ##  ---                                                                                 
    ## 276:                                                                                 
    ## 277:                                                                                 
    ## 278:                                                                                 
    ## 279:                                                                                 
    ## 280:                                                                                 
    ##      requestParameters.AccessControlPolicy.AccessControlList.Grant{}.Permission
    ##   1:                                                                           
    ##   2:                                                                           
    ##   3:                                                                           
    ##   4:                                                                           
    ##   5:                                                                           
    ##  ---                                                                           
    ## 276:                                                                           
    ## 277:                                                                           
    ## 278:                                                                           
    ## 279:                                                                           
    ## 280:                                                                           
    ##      requestParameters.AccessControlPolicy.Owner.DisplayName
    ##   1:                                                        
    ##   2:                                                        
    ##   3:                                                        
    ##   4:                                                        
    ##   5:                                                        
    ##  ---                                                        
    ## 276:                                                        
    ## 277:                                                        
    ## 278:                                                        
    ## 279:                                                        
    ## 280:                                                        
    ##      requestParameters.AccessControlPolicy.Owner.ID
    ##   1:                                               
    ##   2:                                               
    ##   3:                                               
    ##   4:                                               
    ##   5:                                               
    ##  ---                                               
    ## 276:                                               
    ## 277:                                               
    ## 278:                                               
    ## 279:                                               
    ## 280:                                               
    ##      requestParameters.AccessControlPolicy.xmlns
    ##   1:                                            
    ##   2:                                            
    ##   3:                                            
    ##   4:                                            
    ##   5:                                            
    ##  ---                                            
    ## 276:                                            
    ## 277:                                            
    ## 278:                                            
    ## 279:                                            
    ## 280:                                            
    ##      requestParameters.DescribeHostsRequest.Filter.Name
    ##   1:                                                   
    ##   2:                                                   
    ##   3:                                                   
    ##   4:                                                   
    ##   5:                                                   
    ##  ---                                                   
    ## 276:                                                   
    ## 277:                                                   
    ## 278:                                                   
    ## 279:                                                   
    ## 280:                                                   
    ##      requestParameters.DescribeHostsRequest.Filter.Value.content
    ##   1:                                                            
    ##   2:                                                            
    ##   3:                                                            
    ##   4:                                                            
    ##   5:                                                            
    ##  ---                                                            
    ## 276:                                                            
    ## 277:                                                            
    ## 278:                                                            
    ## 279:                                                            
    ## 280:                                                            
    ##      requestParameters.DescribeHostsRequest.Filter.Value.tag
    ##   1:                                                      NA
    ##   2:                                                      NA
    ##   3:                                                      NA
    ##   4:                                                      NA
    ##   5:                                                      NA
    ##  ---                                                        
    ## 276:                                                      NA
    ## 277:                                                      NA
    ## 278:                                                      NA
    ## 279:                                                      NA
    ## 280:                                                      NA
    ##      requestParameters.DescribeHostsRequest.Filter.tag
    ##   1:                                                NA
    ##   2:                                                NA
    ##   3:                                                NA
    ##   4:                                                NA
    ##   5:                                                NA
    ##  ---                                                  
    ## 276:                                                NA
    ## 277:                                                NA
    ## 278:                                                NA
    ## 279:                                                NA
    ## 280:                                                NA
    ##      requestParameters.DescribeInstanceCreditSpecificationsRequest.InstanceId.content
    ##   1:                                                                                 
    ##   2:                                                                                 
    ##   3:                                                                                 
    ##   4:                                                                                 
    ##   5:                                                                                 
    ##  ---                                                                                 
    ## 276:                                                                                 
    ## 277:                                                                                 
    ## 278:                                                                                 
    ## 279:                                                                                 
    ## 280:                                                                                 
    ##      requestParameters.DescribeInstanceCreditSpecificationsRequest.InstanceId.tag
    ##   1:                                                                           NA
    ##   2:                                                                           NA
    ##   3:                                                                           NA
    ##   4:                                                                           NA
    ##   5:                                                                           NA
    ##  ---                                                                             
    ## 276:                                                                           NA
    ## 277:                                                                           NA
    ## 278:                                                                           NA
    ## 279:                                                                           NA
    ## 280:                                                                           NA
    ##      requestParameters.DescribeLaunchTemplateVersionsRequest.LaunchTemplateName
    ##   1:                                                                           
    ##   2:                                                                           
    ##   3:                                                                           
    ##   4:                                                                           
    ##   5:                                                                           
    ##  ---                                                                           
    ## 276:                                                                           
    ## 277:                                                                           
    ## 278:                                                                           
    ## 279:                                                                           
    ## 280:                                                                           
    ##      requestParameters.DescribeLaunchTemplateVersionsRequest.MaxResults
    ##   1:                                                                 NA
    ##   2:                                                                 NA
    ##   3:                                                                 NA
    ##   4:                                                                 NA
    ##   5:                                                                 NA
    ##  ---                                                                   
    ## 276:                                                                 NA
    ## 277:                                                                 NA
    ## 278:                                                                 NA
    ## 279:                                                                 NA
    ## 280:                                                                 NA
    ##      requestParameters.DescribeLaunchTemplatesRequest.MaxResults
    ##   1:                                                          NA
    ##   2:                                                          NA
    ##   3:                                                          NA
    ##   4:                                                          NA
    ##   5:                                                          NA
    ##  ---                                                            
    ## 276:                                                          NA
    ## 277:                                                          NA
    ## 278:                                                          NA
    ## 279:                                                          NA
    ## 280:                                                          NA
    ##      requestParameters.DescribeStaleSecurityGroupsRequest.MaxResults
    ##   1:                                                              NA
    ##   2:                                                              NA
    ##   3:                                                              NA
    ##   4:                                                              NA
    ##   5:                                                              NA
    ##  ---                                                                
    ## 276:                                                              NA
    ## 277:                                                              NA
    ## 278:                                                              NA
    ## 279:                                                              NA
    ## 280:                                                              NA
    ##      requestParameters.DescribeStaleSecurityGroupsRequest.VpcId
    ##   1:                                                           
    ##   2:                                                           
    ##   3:                                                           
    ##   4:                                                           
    ##   5:                                                           
    ##  ---                                                           
    ## 276:                                                           
    ## 277:                                                           
    ## 278:                                                           
    ## 279:                                                           
    ## 280:                                                           
    ##      requestParameters.DescribeVolumesModificationsRequest.MaxResults
    ##   1:                                                               NA
    ##   2:                                                               NA
    ##   3:                                                               NA
    ##   4:                                                               NA
    ##   5:                                                               NA
    ##  ---                                                                 
    ## 276:                                                               NA
    ## 277:                                                               NA
    ## 278:                                                               NA
    ## 279:                                                               NA
    ## 280:                                                               NA
    ##      requestParameters.GetConsoleScreenshotRequest.InstanceId
    ##   1:                                                         
    ##   2:                                                         
    ##   3:                                                         
    ##   4:                                                         
    ##   5:                                                         
    ##  ---                                                         
    ## 276:                                                         
    ## 277:                                                         
    ## 278:                                                         
    ## 279:                                                         
    ## 280:                                                         
    ##      requestParameters.GetConsoleScreenshotRequest.WakeUp
    ##   1:                                                   NA
    ##   2:                                                   NA
    ##   3:                                                   NA
    ##   4:                                                   NA
    ##   5:                                                   NA
    ##  ---                                                     
    ## 276:                                                   NA
    ## 277:                                                   NA
    ## 278:                                                   NA
    ## 279:                                                   NA
    ## 280:                                                   NA
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.GroupId
    ##   1:                                                                            
    ##   2:                                                                            
    ##   3:                                                                            
    ##   4:                                                                            
    ##   5:                                                                            
    ##  ---                                                                            
    ## 276:                                                                            
    ## 277:                                                                            
    ## 278:                                                                            
    ## 279:                                                                            
    ## 280:                                                                            
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.FromPort
    ##   1:                                                                                             
    ##   2:                                                                                             
    ##   3:                                                                                             
    ##   4:                                                                                             
    ##   5:                                                                                             
    ##  ---                                                                                             
    ## 276:                                                                                             
    ## 277:                                                                                             
    ## 278:                                                                                             
    ## 279:                                                                                             
    ## 280:                                                                                             
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.IpProtocol
    ##   1:                                                                                               
    ##   2:                                                                                               
    ##   3:                                                                                               
    ##   4:                                                                                               
    ##   5:                                                                                               
    ##  ---                                                                                               
    ## 276:                                                                                               
    ## 277:                                                                                               
    ## 278:                                                                                               
    ## 279:                                                                                               
    ## 280:                                                                                               
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.IpRanges.CidrIp
    ##   1:                                                                                                    
    ##   2:                                                                                                    
    ##   3:                                                                                                    
    ##   4:                                                                                                    
    ##   5:                                                                                                    
    ##  ---                                                                                                    
    ## 276:                                                                                                    
    ## 277:                                                                                                    
    ## 278:                                                                                                    
    ## 279:                                                                                                    
    ## 280:                                                                                                    
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.IpRanges.Description
    ##   1:                                                                                                         
    ##   2:                                                                                                         
    ##   3:                                                                                                         
    ##   4:                                                                                                         
    ##   5:                                                                                                         
    ##  ---                                                                                                         
    ## 276:                                                                                                         
    ## 277:                                                                                                         
    ## 278:                                                                                                         
    ## 279:                                                                                                         
    ## 280:                                                                                                         
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.IpRanges.tag
    ##   1:                                                                                               NA
    ##   2:                                                                                               NA
    ##   3:                                                                                               NA
    ##   4:                                                                                               NA
    ##   5:                                                                                               NA
    ##  ---                                                                                                 
    ## 276:                                                                                               NA
    ## 277:                                                                                               NA
    ## 278:                                                                                               NA
    ## 279:                                                                                               NA
    ## 280:                                                                                               NA
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.Ipv6Ranges.CidrIpv6
    ##   1:                                                                                                        
    ##   2:                                                                                                        
    ##   3:                                                                                                        
    ##   4:                                                                                                        
    ##   5:                                                                                                        
    ##  ---                                                                                                        
    ## 276:                                                                                                        
    ## 277:                                                                                                        
    ## 278:                                                                                                        
    ## 279:                                                                                                        
    ## 280:                                                                                                        
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.Ipv6Ranges.Description
    ##   1:                                                                                                           
    ##   2:                                                                                                           
    ##   3:                                                                                                           
    ##   4:                                                                                                           
    ##   5:                                                                                                           
    ##  ---                                                                                                           
    ## 276:                                                                                                           
    ## 277:                                                                                                           
    ## 278:                                                                                                           
    ## 279:                                                                                                           
    ## 280:                                                                                                           
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.Ipv6Ranges.tag
    ##   1:                                                                                                 NA
    ##   2:                                                                                                 NA
    ##   3:                                                                                                 NA
    ##   4:                                                                                                 NA
    ##   5:                                                                                                 NA
    ##  ---                                                                                                   
    ## 276:                                                                                                 NA
    ## 277:                                                                                                 NA
    ## 278:                                                                                                 NA
    ## 279:                                                                                                 NA
    ## 280:                                                                                                 NA
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.ToPort
    ##   1:                                                                                           
    ##   2:                                                                                           
    ##   3:                                                                                           
    ##   4:                                                                                           
    ##   5:                                                                                           
    ##  ---                                                                                           
    ## 276:                                                                                           
    ## 277:                                                                                           
    ## 278:                                                                                           
    ## 279:                                                                                           
    ## 280:                                                                                           
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.tag
    ##   1:                                                                                        
    ##   2:                                                                                        
    ##   3:                                                                                        
    ##   4:                                                                                        
    ##   5:                                                                                        
    ##  ---                                                                                        
    ## 276:                                                                                        
    ## 277:                                                                                        
    ## 278:                                                                                        
    ## 279:                                                                                        
    ## 280:                                                                                        
    ##      requestParameters.accessKeyId
    ##   1:                              
    ##   2:                              
    ##   3:                              
    ##   4:                              
    ##   5:                              
    ##  ---                              
    ## 276:                              
    ## 277:                              
    ## 278:                              
    ## 279:                              
    ## 280:                              
    ##      requestParameters.accountAttributeNameSet.items{}.attributeName
    ##   1:                                                                
    ##   2:                                                                
    ##   3:                                                                
    ##   4:                                                                
    ##   5:                                                                
    ##  ---                                                                
    ## 276:                                                                
    ## 277:                                                                
    ## 278:                                                                
    ## 279:                                                                
    ## 280:                                                                
    ##      requestParameters.acl{} requestParameters.attribute
    ##   1:                      NA                            
    ##   2:                      NA                            
    ##   3:                      NA                            
    ##   4:                      NA                            
    ##   5:                      NA                            
    ##  ---                                                    
    ## 276:                      NA                            
    ## 277:                      NA                            
    ## 278:                      NA                            
    ## 279:                      NA                            
    ## 280:                      NA                            
    ##      requestParameters.autoScalingGroupName
    ##   1:                                       
    ##   2:                                       
    ##   3:                                       
    ##   4:                                       
    ##   5:                                       
    ##  ---                                       
    ## 276:                                       
    ## 277:                                       
    ## 278:                                       
    ## 279:                                       
    ## 280:                                       
    ##      requestParameters.autoScalingGroupNames{}
    ##   1:                                          
    ##   2:                                          
    ##   3:                                          
    ##   4:                                          
    ##   5:                                          
    ##  ---                                          
    ## 276:                                          
    ## 277:                                          
    ## 278:                                          
    ## 279:                                          
    ## 280:                                          
    ##      requestParameters.blockDeviceMapping.items{}.deviceName
    ##   1:                                                        
    ##   2:                                                        
    ##   3:                                                        
    ##   4:                                                        
    ##   5:                                                        
    ##  ---                                                        
    ## 276:                                                        
    ## 277:                                                        
    ## 278:                                                        
    ## 279:                                                        
    ## 280:                                                        
    ##      requestParameters.blockDeviceMapping.items{}.ebs.deleteOnTermination
    ##   1:                                                                   NA
    ##   2:                                                                   NA
    ##   3:                                                                   NA
    ##   4:                                                                   NA
    ##   5:                                                                   NA
    ##  ---                                                                     
    ## 276:                                                                   NA
    ## 277:                                                                   NA
    ## 278:                                                                   NA
    ## 279:                                                                   NA
    ## 280:                                                                   NA
    ##      requestParameters.blockDeviceMapping.items{}.ebs.volumeType
    ##   1:                                                            
    ##   2:                                                            
    ##   3:                                                            
    ##   4:                                                            
    ##   5:                                                            
    ##  ---                                                            
    ## 276:                                                            
    ## 277:                                                            
    ## 278:                                                            
    ## 279:                                                            
    ## 280:                                                            
    ##      requestParameters.bucketName requestParameters.configRuleName
    ##   1:                                                              
    ##   2:                                                              
    ##   3:                                                              
    ##   4:                                                              
    ##   5:                                                              
    ##  ---                                                              
    ## 276:                                                              
    ## 277:                                                              
    ## 278:                                                              
    ## 279:                                                              
    ## 280:                                                              
    ##      requestParameters.configRuleNames{} requestParameters.cors{}
    ##   1:                                                           NA
    ##   2:                                                           NA
    ##   3:                                                           NA
    ##   4:                                                           NA
    ##   5:                                                           NA
    ##  ---                                                             
    ## 276:                                                           NA
    ## 277:                                                           NA
    ## 278:                                                           NA
    ## 279:                                                           NA
    ## 280:                                                           NA
    ##      requestParameters.disableApiTermination requestParameters.durationSeconds
    ##   1:                                    TRUE                                NA
    ##   2:                                    TRUE                                NA
    ##   3:                                    TRUE                                NA
    ##   4:                                    TRUE                                NA
    ##   5:                                    TRUE                                NA
    ##  ---                                                                          
    ## 276:                                    TRUE                                NA
    ## 277:                                    TRUE                                NA
    ## 278:                                    TRUE                                NA
    ## 279:                                    TRUE                                NA
    ## 280:                                    TRUE                                NA
    ##      requestParameters.encryptionContext.aws:lambda:FunctionArn
    ##   1:                                                           
    ##   2:                                                           
    ##   3:                                                           
    ##   4:                                                           
    ##   5:                                                           
    ##  ---                                                           
    ## 276:                                                           
    ## 277:                                                           
    ## 278:                                                           
    ## 279:                                                           
    ## 280:                                                           
    ##      requestParameters.encryption{}
    ##   1:                             NA
    ##   2:                             NA
    ##   3:                             NA
    ##   4:                             NA
    ##   5:                             NA
    ##  ---                               
    ## 276:                             NA
    ## 277:                             NA
    ## 278:                             NA
    ## 279:                             NA
    ## 280:                             NA
    ##      requestParameters.filter.completionTimeRange.beginDate
    ##   1:                                                       
    ##   2:                                                       
    ##   3:                                                       
    ##   4:                                                       
    ##   5:                                                       
    ##  ---                                                       
    ## 276:                                                       
    ## 277:                                                       
    ## 278:                                                       
    ## 279:                                                       
    ## 280:                                                       
    ##      requestParameters.filter.completionTimeRange.endDate
    ##   1:                                                     
    ##   2:                                                     
    ##   3:                                                     
    ##   4:                                                     
    ##   5:                                                     
    ##  ---                                                     
    ## 276:                                                     
    ## 277:                                                     
    ## 278:                                                     
    ## 279:                                                     
    ## 280:                                                     
    ##      requestParameters.filter.creationTimeRange.beginDate
    ##   1:                                                     
    ##   2:                                                     
    ##   3:                                                     
    ##   4:                                                     
    ##   5:                                                     
    ##  ---                                                     
    ## 276:                                                     
    ## 277:                                                     
    ## 278:                                                     
    ## 279:                                                     
    ## 280:                                                     
    ##      requestParameters.filter.creationTimeRange.endDate
    ##   1:                                                   
    ##   2:                                                   
    ##   3:                                                   
    ##   4:                                                   
    ##   5:                                                   
    ##  ---                                                   
    ## 276:                                                   
    ## 277:                                                   
    ## 278:                                                   
    ## 279:                                                   
    ## 280:                                                   
    ##      requestParameters.filterSet.items{}.name
    ##   1:                                         
    ##   2:                                         
    ##   3:                                         
    ##   4:                                         
    ##   5:                                         
    ##  ---                                         
    ## 276:                                         
    ## 277:                                         
    ## 278:                                         
    ## 279:                                         
    ## 280:                                         
    ##      requestParameters.filterSet.items{}.valueSet.items{}.value
    ##   1:                                                           
    ##   2:                                                           
    ##   3:                                                           
    ##   4:                                                           
    ##   5:                                                           
    ##  ---                                                           
    ## 276:                                                           
    ## 277:                                                           
    ## 278:                                                           
    ## 279:                                                           
    ## 280:                                                           
    ##      requestParameters.groupId requestParameters.imagesSet.items{}.imageId
    ##   1:                                                                      
    ##   2:                                                                      
    ##   3:                                                                      
    ##   4:                                                                      
    ##   5:                                                                      
    ##  ---                                                                      
    ## 276:                                                                      
    ## 277:                                                                      
    ## 278:                                                                      
    ## 279:                                                                      
    ## 280:                                                                      
    ##      requestParameters.includeAllInstances requestParameters.instanceId
    ##   1:                                    NA                             
    ##   2:                                    NA                             
    ##   3:                                    NA                             
    ##   4:                                    NA                             
    ##   5:                                    NA                             
    ##  ---                                                                   
    ## 276:                                    NA                             
    ## 277:                                    NA                             
    ## 278:                                    NA                             
    ## 279:                                    NA                             
    ## 280:                                    NA                             
    ##      requestParameters.instanceType
    ##   1:                    x1e.8xlarge
    ##   2:                     h1.4xlarge
    ##   3:                   x1e.32xlarge
    ##   4:                    c5.18xlarge
    ##   5:                    i3.16xlarge
    ##  ---                               
    ## 276:                     c5.2xlarge
    ## 277:                    c5.18xlarge
    ## 278:                     i3.8xlarge
    ## 279:                    r4.16xlarge
    ## 280:                     c5.4xlarge
    ##      requestParameters.instancesSet.items{}.imageId
    ##   1:                                   ami-4d46d534
    ##   2:                                   ami-4d46d534
    ##   3:                                   ami-4d46d534
    ##   4:                                   ami-4d46d534
    ##   5:                                   ami-4d46d534
    ##  ---                                               
    ## 276:                                   ami-67973709
    ## 277:                                   ami-67973709
    ## 278:                                   ami-d7aab2b3
    ## 279:                                   ami-d7aab2b3
    ## 280:                                   ami-d7aab2b3
    ##      requestParameters.instancesSet.items{}.instanceId
    ##   1:                                                  
    ##   2:                                                  
    ##   3:                                                  
    ##   4:                                                  
    ##   5:                                                  
    ##  ---                                                  
    ## 276:                                                  
    ## 277:                                                  
    ## 278:                                                  
    ## 279:                                                  
    ## 280:                                                  
    ##      requestParameters.instancesSet.items{}.maxCount
    ##   1:                                              10
    ##   2:                                              10
    ##   3:                                              10
    ##   4:                                              10
    ##   5:                                              10
    ##  ---                                                
    ## 276:                                              10
    ## 277:                                              10
    ## 278:                                              10
    ## 279:                                              10
    ## 280:                                              10
    ##      requestParameters.instancesSet.items{}.minCount
    ##   1:                                               1
    ##   2:                                               1
    ##   3:                                               1
    ##   4:                                               1
    ##   5:                                               1
    ##  ---                                                
    ## 276:                                               1
    ## 277:                                               1
    ## 278:                                               1
    ## 279:                                               1
    ## 280:                                               1
    ##      requestParameters.ipPermissions.items{}.fromPort
    ##   1:                                                 
    ##   2:                                                 
    ##   3:                                                 
    ##   4:                                                 
    ##   5:                                                 
    ##  ---                                                 
    ## 276:                                                 
    ## 277:                                                 
    ## 278:                                                 
    ## 279:                                                 
    ## 280:                                                 
    ##      requestParameters.ipPermissions.items{}.ipProtocol
    ##   1:                                                   
    ##   2:                                                   
    ##   3:                                                   
    ##   4:                                                   
    ##   5:                                                   
    ##  ---                                                   
    ## 276:                                                   
    ## 277:                                                   
    ## 278:                                                   
    ## 279:                                                   
    ## 280:                                                   
    ##      requestParameters.ipPermissions.items{}.ipRanges.items{}.cidrIp
    ##   1:                                                                
    ##   2:                                                                
    ##   3:                                                                
    ##   4:                                                                
    ##   5:                                                                
    ##  ---                                                                
    ## 276:                                                                
    ## 277:                                                                
    ## 278:                                                                
    ## 279:                                                                
    ## 280:                                                                
    ##      requestParameters.ipPermissions.items{}.ipRanges.items{}.description
    ##   1:                                                                     
    ##   2:                                                                     
    ##   3:                                                                     
    ##   4:                                                                     
    ##   5:                                                                     
    ##  ---                                                                     
    ## 276:                                                                     
    ## 277:                                                                     
    ## 278:                                                                     
    ## 279:                                                                     
    ## 280:                                                                     
    ##      requestParameters.ipPermissions.items{}.ipv6Ranges.items{}.cidrIpv6
    ##   1:                                                                    
    ##   2:                                                                    
    ##   3:                                                                    
    ##   4:                                                                    
    ##   5:                                                                    
    ##  ---                                                                    
    ## 276:                                                                    
    ## 277:                                                                    
    ## 278:                                                                    
    ## 279:                                                                    
    ## 280:                                                                    
    ##      requestParameters.ipPermissions.items{}.ipv6Ranges.items{}.description
    ##   1:                                                                       
    ##   2:                                                                       
    ##   3:                                                                       
    ##   4:                                                                       
    ##   5:                                                                       
    ##  ---                                                                       
    ## 276:                                                                       
    ## 277:                                                                       
    ## 278:                                                                       
    ## 279:                                                                       
    ## 280:                                                                       
    ##      requestParameters.ipPermissions.items{}.toPort
    ##   1:                                               
    ##   2:                                               
    ##   3:                                               
    ##   4:                                               
    ##   5:                                               
    ##  ---                                               
    ## 276:                                               
    ## 277:                                               
    ## 278:                                               
    ## 279:                                               
    ## 280:                                               
    ##      requestParameters.lifecycle{} requestParameters.limit
    ##   1:                            NA                      NA
    ##   2:                            NA                      NA
    ##   3:                            NA                      NA
    ##   4:                            NA                      NA
    ##   5:                            NA                      NA
    ##  ---                                                      
    ## 276:                            NA                      NA
    ## 277:                            NA                      NA
    ## 278:                            NA                      NA
    ## 279:                            NA                      NA
    ## 280:                            NA                      NA
    ##      requestParameters.loadBalancerArn requestParameters.location{}
    ##   1:                                                             NA
    ##   2:                                                             NA
    ##   3:                                                             NA
    ##   4:                                                             NA
    ##   5:                                                             NA
    ##  ---                                                               
    ## 276:                                                             NA
    ## 277:                                                             NA
    ## 278:                                                             NA
    ## 279:                                                             NA
    ## 280:                                                             NA
    ##      requestParameters.logging{} requestParameters.maxItems
    ##   1:                          NA                         NA
    ##   2:                          NA                         NA
    ##   3:                          NA                         NA
    ##   4:                          NA                         NA
    ##   5:                          NA                         NA
    ##  ---                                                       
    ## 276:                          NA                         NA
    ## 277:                          NA                         NA
    ## 278:                          NA                         NA
    ## 279:                          NA                         NA
    ## 280:                          NA                         NA
    ##      requestParameters.maxRecords requestParameters.maxResults
    ##   1:                           NA                           NA
    ##   2:                           NA                           NA
    ##   3:                           NA                           NA
    ##   4:                           NA                           NA
    ##   5:                           NA                           NA
    ##  ---                                                          
    ## 276:                           NA                           NA
    ## 277:                           NA                           NA
    ## 278:                           NA                           NA
    ## 279:                           NA                           NA
    ## 280:                           NA                           NA
    ##      requestParameters.monitoring.enabled requestParameters.nextToken
    ##   1:                                FALSE                            
    ##   2:                                FALSE                            
    ##   3:                                FALSE                            
    ##   4:                                FALSE                            
    ##   5:                                FALSE                            
    ##  ---                                                                 
    ## 276:                                FALSE                            
    ## 277:                                FALSE                            
    ## 278:                                FALSE                            
    ## 279:                                FALSE                            
    ## 280:                                FALSE                            
    ##      requestParameters.notification{} requestParameters.ownersSet.items{}.owner
    ##   1:                               NA                                          
    ##   2:                               NA                                          
    ##   3:                               NA                                          
    ##   4:                               NA                                          
    ##   5:                               NA                                          
    ##  ---                                                                           
    ## 276:                               NA                                          
    ## 277:                               NA                                          
    ## 278:                               NA                                          
    ## 279:                               NA                                          
    ## 280:                               NA                                          
    ##      requestParameters.pageSize requestParameters.pathPrefix
    ##   1:                         NA                             
    ##   2:                         NA                             
    ##   3:                         NA                             
    ##   4:                         NA                             
    ##   5:                         NA                             
    ##  ---                                                        
    ## 276:                         NA                             
    ## 277:                         NA                             
    ## 278:                         NA                             
    ## 279:                         NA                             
    ## 280:                         NA                             
    ##      requestParameters.policyName requestParameters.policyNames{}
    ##   1:                                                             
    ##   2:                                                             
    ##   3:                                                             
    ##   4:                                                             
    ##   5:                                                             
    ##  ---                                                             
    ## 276:                                                             
    ## 277:                                                             
    ## 278:                                                             
    ## 279:                                                             
    ## 280:                                                             
    ##      requestParameters.policyType requestParameters.policy{}
    ##   1:                                                      NA
    ##   2:                                                      NA
    ##   3:                                                      NA
    ##   4:                                                      NA
    ##   5:                                                      NA
    ##  ---                                                        
    ## 276:                                                      NA
    ## 277:                                                      NA
    ## 278:                                                      NA
    ## 279:                                                      NA
    ## 280:                                                      NA
    ##      requestParameters.replication{} requestParameters.requestPayment{}
    ##   1:                              NA                                 NA
    ##   2:                              NA                                 NA
    ##   3:                              NA                                 NA
    ##   4:                              NA                                 NA
    ##   5:                              NA                                 NA
    ##  ---                                                                   
    ## 276:                              NA                                 NA
    ## 277:                              NA                                 NA
    ## 278:                              NA                                 NA
    ## 279:                              NA                                 NA
    ## 280:                              NA                                 NA
    ##      requestParameters.resourceArns{}
    ##   1:                                 
    ##   2:                                 
    ##   3:                                 
    ##   4:                                 
    ##   5:                                 
    ##  ---                                 
    ## 276:                                 
    ## 277:                                 
    ## 278:                                 
    ## 279:                                 
    ## 280:                                 
    ##      requestParameters.securityGroupIdSet.items{}.groupId
    ##   1:                                                     
    ##   2:                                                     
    ##   3:                                                     
    ##   4:                                                     
    ##   5:                                                     
    ##  ---                                                     
    ## 276:                                                     
    ## 277:                                                     
    ## 278:                                                     
    ## 279:                                                     
    ## 280:                                                     
    ##      requestParameters.serviceName
    ##   1:                              
    ##   2:                              
    ##   3:                              
    ##   4:                              
    ##   5:                              
    ##  ---                              
    ## 276:                              
    ## 277:                              
    ## 278:                              
    ## 279:                              
    ## 280:                              
    ##      requestParameters.sharedUsersSet.items{}.user requestParameters.status
    ##   1:                                                                       
    ##   2:                                                                       
    ##   3:                                                                       
    ##   4:                                                                       
    ##   5:                                                                       
    ##  ---                                                                       
    ## 276:                                                                       
    ## 277:                                                                       
    ## 278:                                                                       
    ## 279:                                                                       
    ## 280:                                                                       
    ##      requestParameters.tagSpecificationSet.items{}.resourceType
    ##   1:                                                   instance
    ##   2:                                                   instance
    ##   3:                                                   instance
    ##   4:                                                   instance
    ##   5:                                                   instance
    ##  ---                                                           
    ## 276:                                                   instance
    ## 277:                                                   instance
    ## 278:                                                   instance
    ## 279:                                                   instance
    ## 280:                                                   instance
    ##      requestParameters.tagSpecificationSet.items{}.tags{}.key
    ##   1:                                                 my_i_key
    ##   2:                                                 my_i_key
    ##   3:                                                 my_i_key
    ##   4:                                                 my_i_key
    ##   5:                                                 my_i_key
    ##  ---                                                         
    ## 276:                                                 my_i_key
    ## 277:                                                 my_i_key
    ## 278:                                                 my_i_key
    ## 279:                                                 my_i_key
    ## 280:                                                 my_i_key
    ##      requestParameters.tagSpecificationSet.items{}.tags{}.value
    ##   1:                                                   my_i_val
    ##   2:                                                   my_i_val
    ##   3:                                                   my_i_val
    ##   4:                                                   my_i_val
    ##   5:                                                   my_i_val
    ##  ---                                                           
    ## 276:                                                   my_i_val
    ## 277:                                                   my_i_val
    ## 278:                                                   my_i_val
    ## 279:                                                   my_i_val
    ## 280:                                                   my_i_val
    ##      requestParameters.tagging{} requestParameters.targetGroupArn
    ##   1:                          NA                                 
    ##   2:                          NA                                 
    ##   3:                          NA                                 
    ##   4:                          NA                                 
    ##   5:                          NA                                 
    ##  ---                                                             
    ## 276:                          NA                                 
    ## 277:                          NA                                 
    ## 278:                          NA                                 
    ## 279:                          NA                                 
    ## 280:                          NA                                 
    ##      requestParameters.targetTrackingConfiguration.disableScaleIn
    ##   1:                                                           NA
    ##   2:                                                           NA
    ##   3:                                                           NA
    ##   4:                                                           NA
    ##   5:                                                           NA
    ##  ---                                                             
    ## 276:                                                           NA
    ## 277:                                                           NA
    ## 278:                                                           NA
    ## 279:                                                           NA
    ## 280:                                                           NA
    ##      requestParameters.targetTrackingConfiguration.predefinedMetricSpecification.predefinedMetricType
    ##   1:                                                                                                 
    ##   2:                                                                                                 
    ##   3:                                                                                                 
    ##   4:                                                                                                 
    ##   5:                                                                                                 
    ##  ---                                                                                                 
    ## 276:                                                                                                 
    ## 277:                                                                                                 
    ## 278:                                                                                                 
    ## 279:                                                                                                 
    ## 280:                                                                                                 
    ##      requestParameters.targetTrackingConfiguration.targetValue
    ##   1:                                                        NA
    ##   2:                                                        NA
    ##   3:                                                        NA
    ##   4:                                                        NA
    ##   5:                                                        NA
    ##  ---                                                          
    ## 276:                                                        NA
    ## 277:                                                        NA
    ## 278:                                                        NA
    ## 279:                                                        NA
    ## 280:                                                        NA
    ##      requestParameters.userData requestParameters.userName
    ##   1:     <sensitiveDataRemoved>                           
    ##   2:     <sensitiveDataRemoved>                           
    ##   3:     <sensitiveDataRemoved>                           
    ##   4:     <sensitiveDataRemoved>                           
    ##   5:     <sensitiveDataRemoved>                           
    ##  ---                                                      
    ## 276:     <sensitiveDataRemoved>                           
    ## 277:     <sensitiveDataRemoved>                           
    ## 278:     <sensitiveDataRemoved>                           
    ## 279:     <sensitiveDataRemoved>                           
    ## 280:     <sensitiveDataRemoved>                           
    ##      requestParameters.versioning{}
    ##   1:                             NA
    ##   2:                             NA
    ##   3:                             NA
    ##   4:                             NA
    ##   5:                             NA
    ##  ---                               
    ## 276:                             NA
    ## 277:                             NA
    ## 278:                             NA
    ## 279:                             NA
    ## 280:                             NA
    ##      requestParameters.volumeSet.items{}.volumeId requestParameters.website{}
    ##   1:                                                                       NA
    ##   2:                                                                       NA
    ##   3:                                                                       NA
    ##   4:                                                                       NA
    ##   5:                                                                       NA
    ##  ---                                                                         
    ## 276:                                                                       NA
    ## 277:                                                                       NA
    ## 278:                                                                       NA
    ## 279:                                                                       NA
    ## 280:                                                                       NA
    ##      resources{}.ARN resources{}.accountId resources{}.type responseElements
    ##   1:                                    NA                              null
    ##   2:                                    NA                              null
    ##   3:                                    NA                              null
    ##   4:                                    NA                              null
    ##   5:                                    NA                              null
    ##  ---                                                                        
    ## 276:                                    NA                              null
    ## 277:                                    NA                              null
    ## 278:                                    NA                              null
    ## 279:                                    NA                              null
    ## 280:                                    NA                              null
    ##      responseElements.ConsoleLogin
    ##   1:                              
    ##   2:                              
    ##   3:                              
    ##   4:                              
    ##   5:                              
    ##  ---                              
    ## 276:                              
    ## 277:                              
    ## 278:                              
    ## 279:                              
    ## 280:                              
    ##      responseElements.UpdateSecurityGroupRuleDescriptionsIngressResponse.requestId
    ##   1:                                                                              
    ##   2:                                                                              
    ##   3:                                                                              
    ##   4:                                                                              
    ##   5:                                                                              
    ##  ---                                                                              
    ## 276:                                                                              
    ## 277:                                                                              
    ## 278:                                                                              
    ## 279:                                                                              
    ## 280:                                                                              
    ##      responseElements.UpdateSecurityGroupRuleDescriptionsIngressResponse.return
    ##   1:                                                                         NA
    ##   2:                                                                         NA
    ##   3:                                                                         NA
    ##   4:                                                                         NA
    ##   5:                                                                         NA
    ##  ---                                                                           
    ## 276:                                                                         NA
    ## 277:                                                                         NA
    ## 278:                                                                         NA
    ## 279:                                                                         NA
    ## 280:                                                                         NA
    ##      responseElements.UpdateSecurityGroupRuleDescriptionsIngressResponse.xmlns
    ##   1:                                                                          
    ##   2:                                                                          
    ##   3:                                                                          
    ##   4:                                                                          
    ##   5:                                                                          
    ##  ---                                                                          
    ## 276:                                                                          
    ## 277:                                                                          
    ## 278:                                                                          
    ## 279:                                                                          
    ## 280:                                                                          
    ##      responseElements._return responseElements.account
    ##   1:                       NA                       NA
    ##   2:                       NA                       NA
    ##   3:                       NA                       NA
    ##   4:                       NA                       NA
    ##   5:                       NA                       NA
    ##  ---                                                  
    ## 276:                       NA                       NA
    ## 277:                       NA                       NA
    ## 278:                       NA                       NA
    ## 279:                       NA                       NA
    ## 280:                       NA                       NA
    ##      responseElements.alarms{}.alarmARN responseElements.alarms{}.alarmName
    ##   1:                                                                       
    ##   2:                                                                       
    ##   3:                                                                       
    ##   4:                                                                       
    ##   5:                                                                       
    ##  ---                                                                       
    ## 276:                                                                       
    ## 277:                                                                       
    ## 278:                                                                       
    ## 279:                                                                       
    ## 280:                                                                       
    ##      responseElements.arn
    ##   1:                     
    ##   2:                     
    ##   3:                     
    ##   4:                     
    ##   5:                     
    ##  ---                     
    ## 276:                     
    ## 277:                     
    ## 278:                     
    ## 279:                     
    ## 280:                     
    ##      responseElements.complianceSummary.complianceSummaryTimestamp
    ##   1:                                                              
    ##   2:                                                              
    ##   3:                                                              
    ##   4:                                                              
    ##   5:                                                              
    ##  ---                                                              
    ## 276:                                                              
    ## 277:                                                              
    ## 278:                                                              
    ## 279:                                                              
    ## 280:                                                              
    ##      responseElements.complianceSummary.compliantResourceCount.capExceeded
    ##   1:                                                                    NA
    ##   2:                                                                    NA
    ##   3:                                                                    NA
    ##   4:                                                                    NA
    ##   5:                                                                    NA
    ##  ---                                                                      
    ## 276:                                                                    NA
    ## 277:                                                                    NA
    ## 278:                                                                    NA
    ## 279:                                                                    NA
    ## 280:                                                                    NA
    ##      responseElements.complianceSummary.compliantResourceCount.cappedCount
    ##   1:                                                                    NA
    ##   2:                                                                    NA
    ##   3:                                                                    NA
    ##   4:                                                                    NA
    ##   5:                                                                    NA
    ##  ---                                                                      
    ## 276:                                                                    NA
    ## 277:                                                                    NA
    ## 278:                                                                    NA
    ## 279:                                                                    NA
    ## 280:                                                                    NA
    ##      responseElements.complianceSummary.nonCompliantResourceCount.capExceeded
    ##   1:                                                                       NA
    ##   2:                                                                       NA
    ##   3:                                                                       NA
    ##   4:                                                                       NA
    ##   5:                                                                       NA
    ##  ---                                                                         
    ## 276:                                                                       NA
    ## 277:                                                                       NA
    ## 278:                                                                       NA
    ## 279:                                                                       NA
    ## 280:                                                                       NA
    ##      responseElements.complianceSummary.nonCompliantResourceCount.cappedCount
    ##   1:                                                                       NA
    ##   2:                                                                       NA
    ##   3:                                                                       NA
    ##   4:                                                                       NA
    ##   5:                                                                       NA
    ##  ---                                                                         
    ## 276:                                                                       NA
    ## 277:                                                                       NA
    ## 278:                                                                       NA
    ## 279:                                                                       NA
    ## 280:                                                                       NA
    ##      responseElements.configRulesEvaluationStatus{}.configRuleArn
    ##   1:                                                             
    ##   2:                                                             
    ##   3:                                                             
    ##   4:                                                             
    ##   5:                                                             
    ##  ---                                                             
    ## 276:                                                             
    ## 277:                                                             
    ## 278:                                                             
    ## 279:                                                             
    ## 280:                                                             
    ##      responseElements.configRulesEvaluationStatus{}.configRuleId
    ##   1:                                                            
    ##   2:                                                            
    ##   3:                                                            
    ##   4:                                                            
    ##   5:                                                            
    ##  ---                                                            
    ## 276:                                                            
    ## 277:                                                            
    ## 278:                                                            
    ## 279:                                                            
    ## 280:                                                            
    ##      responseElements.configRulesEvaluationStatus{}.configRuleName
    ##   1:                                                              
    ##   2:                                                              
    ##   3:                                                              
    ##   4:                                                              
    ##   5:                                                              
    ##  ---                                                              
    ## 276:                                                              
    ## 277:                                                              
    ## 278:                                                              
    ## 279:                                                              
    ## 280:                                                              
    ##      responseElements.configRulesEvaluationStatus{}.firstActivatedTime
    ##   1:                                                                  
    ##   2:                                                                  
    ##   3:                                                                  
    ##   4:                                                                  
    ##   5:                                                                  
    ##  ---                                                                  
    ## 276:                                                                  
    ## 277:                                                                  
    ## 278:                                                                  
    ## 279:                                                                  
    ## 280:                                                                  
    ##      responseElements.configRulesEvaluationStatus{}.firstEvaluationStarted
    ##   1:                                                                    NA
    ##   2:                                                                    NA
    ##   3:                                                                    NA
    ##   4:                                                                    NA
    ##   5:                                                                    NA
    ##  ---                                                                      
    ## 276:                                                                    NA
    ## 277:                                                                    NA
    ## 278:                                                                    NA
    ## 279:                                                                    NA
    ## 280:                                                                    NA
    ##      responseElements.configRulesEvaluationStatus{}.lastSuccessfulEvaluationTime
    ##   1:                                                                            
    ##   2:                                                                            
    ##   3:                                                                            
    ##   4:                                                                            
    ##   5:                                                                            
    ##  ---                                                                            
    ## 276:                                                                            
    ## 277:                                                                            
    ## 278:                                                                            
    ## 279:                                                                            
    ## 280:                                                                            
    ##      responseElements.configRulesEvaluationStatus{}.lastSuccessfulInvocationTime
    ##   1:                                                                            
    ##   2:                                                                            
    ##   3:                                                                            
    ##   4:                                                                            
    ##   5:                                                                            
    ##  ---                                                                            
    ## 276:                                                                            
    ## 277:                                                                            
    ## 278:                                                                            
    ## 279:                                                                            
    ## 280:                                                                            
    ##      responseElements.configRules{}.configRuleArn
    ##   1:                                             
    ##   2:                                             
    ##   3:                                             
    ##   4:                                             
    ##   5:                                             
    ##  ---                                             
    ## 276:                                             
    ## 277:                                             
    ## 278:                                             
    ## 279:                                             
    ## 280:                                             
    ##      responseElements.configRules{}.configRuleId
    ##   1:                                            
    ##   2:                                            
    ##   3:                                            
    ##   4:                                            
    ##   5:                                            
    ##  ---                                            
    ## 276:                                            
    ## 277:                                            
    ## 278:                                            
    ## 279:                                            
    ## 280:                                            
    ##      responseElements.configRules{}.configRuleName
    ##   1:                                              
    ##   2:                                              
    ##   3:                                              
    ##   4:                                              
    ##   5:                                              
    ##  ---                                              
    ## 276:                                              
    ## 277:                                              
    ## 278:                                              
    ## 279:                                              
    ## 280:                                              
    ##      responseElements.configRules{}.configRuleState
    ##   1:                                               
    ##   2:                                               
    ##   3:                                               
    ##   4:                                               
    ##   5:                                               
    ##  ---                                               
    ## 276:                                               
    ## 277:                                               
    ## 278:                                               
    ## 279:                                               
    ## 280:                                               
    ##      responseElements.configRules{}.description
    ##   1:                                           
    ##   2:                                           
    ##   3:                                           
    ##   4:                                           
    ##   5:                                           
    ##  ---                                           
    ## 276:                                           
    ## 277:                                           
    ## 278:                                           
    ## 279:                                           
    ## 280:                                           
    ##      responseElements.configRules{}.inputParameters
    ##   1:                                               
    ##   2:                                               
    ##   3:                                               
    ##   4:                                               
    ##   5:                                               
    ##  ---                                               
    ## 276:                                               
    ## 277:                                               
    ## 278:                                               
    ## 279:                                               
    ## 280:                                               
    ##      responseElements.configRules{}.maximumExecutionFrequency
    ##   1:                                                         
    ##   2:                                                         
    ##   3:                                                         
    ##   4:                                                         
    ##   5:                                                         
    ##  ---                                                         
    ## 276:                                                         
    ## 277:                                                         
    ## 278:                                                         
    ## 279:                                                         
    ## 280:                                                         
    ##      responseElements.configRules{}.scope.complianceResourceTypes{}
    ##   1:                                                               
    ##   2:                                                               
    ##   3:                                                               
    ##   4:                                                               
    ##   5:                                                               
    ##  ---                                                               
    ## 276:                                                               
    ## 277:                                                               
    ## 278:                                                               
    ## 279:                                                               
    ## 280:                                                               
    ##      responseElements.configRules{}.source.owner
    ##   1:                                            
    ##   2:                                            
    ##   3:                                            
    ##   4:                                            
    ##   5:                                            
    ##  ---                                            
    ## 276:                                            
    ## 277:                                            
    ## 278:                                            
    ## 279:                                            
    ## 280:                                            
    ##      responseElements.configRules{}.source.sourceIdentifier
    ##   1:                                                       
    ##   2:                                                       
    ##   3:                                                       
    ##   4:                                                       
    ##   5:                                                       
    ##  ---                                                       
    ## 276:                                                       
    ## 277:                                                       
    ## 278:                                                       
    ## 279:                                                       
    ## 280:                                                       
    ##      responseElements.credentials.accessKeyId
    ##   1:                                         
    ##   2:                                         
    ##   3:                                         
    ##   4:                                         
    ##   5:                                         
    ##  ---                                         
    ## 276:                                         
    ## 277:                                         
    ## 278:                                         
    ## 279:                                         
    ## 280:                                         
    ##      responseElements.credentials.expiration
    ##   1:                                        
    ##   2:                                        
    ##   3:                                        
    ##   4:                                        
    ##   5:                                        
    ##  ---                                        
    ## 276:                                        
    ## 277:                                        
    ## 278:                                        
    ## 279:                                        
    ## 280:                                        
    ##      responseElements.credentials.sessionToken
    ##   1:                                          
    ##   2:                                          
    ##   3:                                          
    ##   4:                                          
    ##   5:                                          
    ##  ---                                          
    ## 276:                                          
    ## 277:                                          
    ## 278:                                          
    ## 279:                                          
    ## 280:                                          
    ##      responseElements.evaluationResults{}.annotation
    ##   1:                                                
    ##   2:                                                
    ##   3:                                                
    ##   4:                                                
    ##   5:                                                
    ##  ---                                                
    ## 276:                                                
    ## 277:                                                
    ## 278:                                                
    ## 279:                                                
    ## 280:                                                
    ##      responseElements.evaluationResults{}.complianceType
    ##   1:                                                    
    ##   2:                                                    
    ##   3:                                                    
    ##   4:                                                    
    ##   5:                                                    
    ##  ---                                                    
    ## 276:                                                    
    ## 277:                                                    
    ## 278:                                                    
    ## 279:                                                    
    ## 280:                                                    
    ##      responseElements.evaluationResults{}.configRuleInvokedTime
    ##   1:                                                           
    ##   2:                                                           
    ##   3:                                                           
    ##   4:                                                           
    ##   5:                                                           
    ##  ---                                                           
    ## 276:                                                           
    ## 277:                                                           
    ## 278:                                                           
    ## 279:                                                           
    ## 280:                                                           
    ##      responseElements.evaluationResults{}.evaluationResultIdentifier.evaluationResultQualifier.configRuleName
    ##   1:                                                                                                         
    ##   2:                                                                                                         
    ##   3:                                                                                                         
    ##   4:                                                                                                         
    ##   5:                                                                                                         
    ##  ---                                                                                                         
    ## 276:                                                                                                         
    ## 277:                                                                                                         
    ## 278:                                                                                                         
    ## 279:                                                                                                         
    ## 280:                                                                                                         
    ##      responseElements.evaluationResults{}.evaluationResultIdentifier.evaluationResultQualifier.resourceId
    ##   1:                                                                                                     
    ##   2:                                                                                                     
    ##   3:                                                                                                     
    ##   4:                                                                                                     
    ##   5:                                                                                                     
    ##  ---                                                                                                     
    ## 276:                                                                                                     
    ## 277:                                                                                                     
    ## 278:                                                                                                     
    ## 279:                                                                                                     
    ## 280:                                                                                                     
    ##      responseElements.evaluationResults{}.evaluationResultIdentifier.evaluationResultQualifier.resourceType
    ##   1:                                                                                                       
    ##   2:                                                                                                       
    ##   3:                                                                                                       
    ##   4:                                                                                                       
    ##   5:                                                                                                       
    ##  ---                                                                                                       
    ## 276:                                                                                                       
    ## 277:                                                                                                       
    ## 278:                                                                                                       
    ## 279:                                                                                                       
    ## 280:                                                                                                       
    ##      responseElements.evaluationResults{}.evaluationResultIdentifier.orderingTimestamp
    ##   1:                                                                                  
    ##   2:                                                                                  
    ##   3:                                                                                  
    ##   4:                                                                                  
    ##   5:                                                                                  
    ##  ---                                                                                  
    ## 276:                                                                                  
    ## 277:                                                                                  
    ## 278:                                                                                  
    ## 279:                                                                                  
    ## 280:                                                                                  
    ##      responseElements.evaluationResults{}.resultRecordedTime
    ##   1:                                                        
    ##   2:                                                        
    ##   3:                                                        
    ##   4:                                                        
    ##   5:                                                        
    ##  ---                                                        
    ## 276:                                                        
    ## 277:                                                        
    ## 278:                                                        
    ## 279:                                                        
    ## 280:                                                        
    ##      responseElements.instancesSet.items{}.currentState.code
    ##   1:                                                        
    ##   2:                                                        
    ##   3:                                                        
    ##   4:                                                        
    ##   5:                                                        
    ##  ---                                                        
    ## 276:                                                        
    ## 277:                                                        
    ## 278:                                                        
    ## 279:                                                        
    ## 280:                                                        
    ##      responseElements.instancesSet.items{}.currentState.name
    ##   1:                                                        
    ##   2:                                                        
    ##   3:                                                        
    ##   4:                                                        
    ##   5:                                                        
    ##  ---                                                        
    ## 276:                                                        
    ## 277:                                                        
    ## 278:                                                        
    ## 279:                                                        
    ## 280:                                                        
    ##      responseElements.instancesSet.items{}.instanceId
    ##   1:                                                 
    ##   2:                                                 
    ##   3:                                                 
    ##   4:                                                 
    ##   5:                                                 
    ##  ---                                                 
    ## 276:                                                 
    ## 277:                                                 
    ## 278:                                                 
    ## 279:                                                 
    ## 280:                                                 
    ##      responseElements.instancesSet.items{}.previousState.code
    ##   1:                                                         
    ##   2:                                                         
    ##   3:                                                         
    ##   4:                                                         
    ##   5:                                                         
    ##  ---                                                         
    ## 276:                                                         
    ## 277:                                                         
    ## 278:                                                         
    ## 279:                                                         
    ## 280:                                                         
    ##      responseElements.instancesSet.items{}.previousState.name
    ##   1:                                                         
    ##   2:                                                         
    ##   3:                                                         
    ##   4:                                                         
    ##   5:                                                         
    ##  ---                                                         
    ## 276:                                                         
    ## 277:                                                         
    ## 278:                                                         
    ## 279:                                                         
    ## 280:                                                         
    ##      responseElements.isTruncated
    ##   1:                           NA
    ##   2:                           NA
    ##   3:                           NA
    ##   4:                           NA
    ##   5:                           NA
    ##  ---                             
    ## 276:                           NA
    ## 277:                           NA
    ## 278:                           NA
    ## 279:                           NA
    ## 280:                           NA
    ##      responseElements.listeners{}.defaultActions{}.targetGroupArn
    ##   1:                                                             
    ##   2:                                                             
    ##   3:                                                             
    ##   4:                                                             
    ##   5:                                                             
    ##  ---                                                             
    ## 276:                                                             
    ## 277:                                                             
    ## 278:                                                             
    ## 279:                                                             
    ## 280:                                                             
    ##      responseElements.listeners{}.defaultActions{}.type
    ##   1:                                                   
    ##   2:                                                   
    ##   3:                                                   
    ##   4:                                                   
    ##   5:                                                   
    ##  ---                                                   
    ## 276:                                                   
    ## 277:                                                   
    ## 278:                                                   
    ## 279:                                                   
    ## 280:                                                   
    ##      responseElements.listeners{}.listenerArn
    ##   1:                                         
    ##   2:                                         
    ##   3:                                         
    ##   4:                                         
    ##   5:                                         
    ##  ---                                         
    ## 276:                                         
    ## 277:                                         
    ## 278:                                         
    ## 279:                                         
    ## 280:                                         
    ##      responseElements.listeners{}.loadBalancerArn
    ##   1:                                             
    ##   2:                                             
    ##   3:                                             
    ##   4:                                             
    ##   5:                                             
    ##  ---                                             
    ## 276:                                             
    ## 277:                                             
    ## 278:                                             
    ## 279:                                             
    ## 280:                                             
    ##      responseElements.listeners{}.port responseElements.listeners{}.protocol
    ##   1:                                NA                                      
    ##   2:                                NA                                      
    ##   3:                                NA                                      
    ##   4:                                NA                                      
    ##   5:                                NA                                      
    ##  ---                                                                        
    ## 276:                                NA                                      
    ## 277:                                NA                                      
    ## 278:                                NA                                      
    ## 279:                                NA                                      
    ## 280:                                NA                                      
    ##      responseElements.loadBalancers{}.availabilityZones{}.subnetId
    ##   1:                                                              
    ##   2:                                                              
    ##   3:                                                              
    ##   4:                                                              
    ##   5:                                                              
    ##  ---                                                              
    ## 276:                                                              
    ## 277:                                                              
    ## 278:                                                              
    ## 279:                                                              
    ## 280:                                                              
    ##      responseElements.loadBalancers{}.availabilityZones{}.zoneName
    ##   1:                                                              
    ##   2:                                                              
    ##   3:                                                              
    ##   4:                                                              
    ##   5:                                                              
    ##  ---                                                              
    ## 276:                                                              
    ## 277:                                                              
    ## 278:                                                              
    ## 279:                                                              
    ## 280:                                                              
    ##      responseElements.loadBalancers{}.canonicalHostedZoneId
    ##   1:                                                       
    ##   2:                                                       
    ##   3:                                                       
    ##   4:                                                       
    ##   5:                                                       
    ##  ---                                                       
    ## 276:                                                       
    ## 277:                                                       
    ## 278:                                                       
    ## 279:                                                       
    ## 280:                                                       
    ##      responseElements.loadBalancers{}.createdTime
    ##   1:                                             
    ##   2:                                             
    ##   3:                                             
    ##   4:                                             
    ##   5:                                             
    ##  ---                                             
    ## 276:                                             
    ## 277:                                             
    ## 278:                                             
    ## 279:                                             
    ## 280:                                             
    ##      responseElements.loadBalancers{}.dNSName
    ##   1:                                         
    ##   2:                                         
    ##   3:                                         
    ##   4:                                         
    ##   5:                                         
    ##  ---                                         
    ## 276:                                         
    ## 277:                                         
    ## 278:                                         
    ## 279:                                         
    ## 280:                                         
    ##      responseElements.loadBalancers{}.ipAddressType
    ##   1:                                               
    ##   2:                                               
    ##   3:                                               
    ##   4:                                               
    ##   5:                                               
    ##  ---                                               
    ## 276:                                               
    ## 277:                                               
    ## 278:                                               
    ## 279:                                               
    ## 280:                                               
    ##      responseElements.loadBalancers{}.loadBalancerArn
    ##   1:                                                 
    ##   2:                                                 
    ##   3:                                                 
    ##   4:                                                 
    ##   5:                                                 
    ##  ---                                                 
    ## 276:                                                 
    ## 277:                                                 
    ## 278:                                                 
    ## 279:                                                 
    ## 280:                                                 
    ##      responseElements.loadBalancers{}.loadBalancerName
    ##   1:                                                  
    ##   2:                                                  
    ##   3:                                                  
    ##   4:                                                  
    ##   5:                                                  
    ##  ---                                                  
    ## 276:                                                  
    ## 277:                                                  
    ## 278:                                                  
    ## 279:                                                  
    ## 280:                                                  
    ##      responseElements.loadBalancers{}.scheme
    ##   1:                                        
    ##   2:                                        
    ##   3:                                        
    ##   4:                                        
    ##   5:                                        
    ##  ---                                        
    ## 276:                                        
    ## 277:                                        
    ## 278:                                        
    ## 279:                                        
    ## 280:                                        
    ##      responseElements.loadBalancers{}.securityGroups{}
    ##   1:                                                  
    ##   2:                                                  
    ##   3:                                                  
    ##   4:                                                  
    ##   5:                                                  
    ##  ---                                                  
    ## 276:                                                  
    ## 277:                                                  
    ## 278:                                                  
    ## 279:                                                  
    ## 280:                                                  
    ##      responseElements.loadBalancers{}.state.code
    ##   1:                                            
    ##   2:                                            
    ##   3:                                            
    ##   4:                                            
    ##   5:                                            
    ##  ---                                            
    ## 276:                                            
    ## 277:                                            
    ## 278:                                            
    ## 279:                                            
    ## 280:                                            
    ##      responseElements.loadBalancers{}.type
    ##   1:                                      
    ##   2:                                      
    ##   3:                                      
    ##   4:                                      
    ##   5:                                      
    ##  ---                                      
    ## 276:                                      
    ## 277:                                      
    ## 278:                                      
    ## 279:                                      
    ## 280:                                      
    ##      responseElements.loadBalancers{}.vpcId responseElements.nextToken
    ##   1:                                                                  
    ##   2:                                                                  
    ##   3:                                                                  
    ##   4:                                                                  
    ##   5:                                                                  
    ##  ---                                                                  
    ## 276:                                                                  
    ## 277:                                                                  
    ## 278:                                                                  
    ## 279:                                                                  
    ## 280:                                                                  
    ##      responseElements.policyARN responseElements.requestId
    ##   1:                                                      
    ##   2:                                                      
    ##   3:                                                      
    ##   4:                                                      
    ##   5:                                                      
    ##  ---                                                      
    ## 276:                                                      
    ## 277:                                                      
    ## 278:                                                      
    ## 279:                                                      
    ## 280:                                                      
    ##      responseElements.tagDescriptions{}.resourceArn
    ##   1:                                               
    ##   2:                                               
    ##   3:                                               
    ##   4:                                               
    ##   5:                                               
    ##  ---                                               
    ## 276:                                               
    ## 277:                                               
    ## 278:                                               
    ## 279:                                               
    ## 280:                                               
    ##      responseElements.targetGroups{}.healthCheckIntervalSeconds
    ##   1:                                                         NA
    ##   2:                                                         NA
    ##   3:                                                         NA
    ##   4:                                                         NA
    ##   5:                                                         NA
    ##  ---                                                           
    ## 276:                                                         NA
    ## 277:                                                         NA
    ## 278:                                                         NA
    ## 279:                                                         NA
    ## 280:                                                         NA
    ##      responseElements.targetGroups{}.healthCheckPath
    ##   1:                                                
    ##   2:                                                
    ##   3:                                                
    ##   4:                                                
    ##   5:                                                
    ##  ---                                                
    ## 276:                                                
    ## 277:                                                
    ## 278:                                                
    ## 279:                                                
    ## 280:                                                
    ##      responseElements.targetGroups{}.healthCheckPort
    ##   1:                                                
    ##   2:                                                
    ##   3:                                                
    ##   4:                                                
    ##   5:                                                
    ##  ---                                                
    ## 276:                                                
    ## 277:                                                
    ## 278:                                                
    ## 279:                                                
    ## 280:                                                
    ##      responseElements.targetGroups{}.healthCheckProtocol
    ##   1:                                                    
    ##   2:                                                    
    ##   3:                                                    
    ##   4:                                                    
    ##   5:                                                    
    ##  ---                                                    
    ## 276:                                                    
    ## 277:                                                    
    ## 278:                                                    
    ## 279:                                                    
    ## 280:                                                    
    ##      responseElements.targetGroups{}.healthCheckTimeoutSeconds
    ##   1:                                                        NA
    ##   2:                                                        NA
    ##   3:                                                        NA
    ##   4:                                                        NA
    ##   5:                                                        NA
    ##  ---                                                          
    ## 276:                                                        NA
    ## 277:                                                        NA
    ## 278:                                                        NA
    ## 279:                                                        NA
    ## 280:                                                        NA
    ##      responseElements.targetGroups{}.healthyThresholdCount
    ##   1:                                                    NA
    ##   2:                                                    NA
    ##   3:                                                    NA
    ##   4:                                                    NA
    ##   5:                                                    NA
    ##  ---                                                      
    ## 276:                                                    NA
    ## 277:                                                    NA
    ## 278:                                                    NA
    ## 279:                                                    NA
    ## 280:                                                    NA
    ##      responseElements.targetGroups{}.loadBalancerArns{}
    ##   1:                                                   
    ##   2:                                                   
    ##   3:                                                   
    ##   4:                                                   
    ##   5:                                                   
    ##  ---                                                   
    ## 276:                                                   
    ## 277:                                                   
    ## 278:                                                   
    ## 279:                                                   
    ## 280:                                                   
    ##      responseElements.targetGroups{}.matcher.httpCode
    ##   1:                                               NA
    ##   2:                                               NA
    ##   3:                                               NA
    ##   4:                                               NA
    ##   5:                                               NA
    ##  ---                                                 
    ## 276:                                               NA
    ## 277:                                               NA
    ## 278:                                               NA
    ## 279:                                               NA
    ## 280:                                               NA
    ##      responseElements.targetGroups{}.port
    ##   1:                                   NA
    ##   2:                                   NA
    ##   3:                                   NA
    ##   4:                                   NA
    ##   5:                                   NA
    ##  ---                                     
    ## 276:                                   NA
    ## 277:                                   NA
    ## 278:                                   NA
    ## 279:                                   NA
    ## 280:                                   NA
    ##      responseElements.targetGroups{}.protocol
    ##   1:                                         
    ##   2:                                         
    ##   3:                                         
    ##   4:                                         
    ##   5:                                         
    ##  ---                                         
    ## 276:                                         
    ## 277:                                         
    ## 278:                                         
    ## 279:                                         
    ## 280:                                         
    ##      responseElements.targetGroups{}.targetGroupArn
    ##   1:                                               
    ##   2:                                               
    ##   3:                                               
    ##   4:                                               
    ##   5:                                               
    ##  ---                                               
    ## 276:                                               
    ## 277:                                               
    ## 278:                                               
    ## 279:                                               
    ## 280:                                               
    ##      responseElements.targetGroups{}.targetGroupName
    ##   1:                                                
    ##   2:                                                
    ##   3:                                                
    ##   4:                                                
    ##   5:                                                
    ##  ---                                                
    ## 276:                                                
    ## 277:                                                
    ## 278:                                                
    ## 279:                                                
    ## 280:                                                
    ##      responseElements.targetGroups{}.targetType
    ##   1:                                           
    ##   2:                                           
    ##   3:                                           
    ##   4:                                           
    ##   5:                                           
    ##  ---                                           
    ## 276:                                           
    ## 277:                                           
    ## 278:                                           
    ## 279:                                           
    ## 280:                                           
    ##      responseElements.targetGroups{}.unhealthyThresholdCount
    ##   1:                                                      NA
    ##   2:                                                      NA
    ##   3:                                                      NA
    ##   4:                                                      NA
    ##   5:                                                      NA
    ##  ---                                                        
    ## 276:                                                      NA
    ## 277:                                                      NA
    ## 278:                                                      NA
    ## 279:                                                      NA
    ## 280:                                                      NA
    ##      responseElements.targetGroups{}.vpcId
    ##   1:                                      
    ##   2:                                      
    ##   3:                                      
    ##   4:                                      
    ##   5:                                      
    ##  ---                                      
    ## 276:                                      
    ## 277:                                      
    ## 278:                                      
    ## 279:                                      
    ## 280:                                      
    ##      responseElements.targetHealthDescriptions{}.healthCheckPort
    ##   1:                                                            
    ##   2:                                                            
    ##   3:                                                            
    ##   4:                                                            
    ##   5:                                                            
    ##  ---                                                            
    ## 276:                                                            
    ## 277:                                                            
    ## 278:                                                            
    ## 279:                                                            
    ## 280:                                                            
    ##      responseElements.targetHealthDescriptions{}.target.id
    ##   1:                                                      
    ##   2:                                                      
    ##   3:                                                      
    ##   4:                                                      
    ##   5:                                                      
    ##  ---                                                      
    ## 276:                                                      
    ## 277:                                                      
    ## 278:                                                      
    ## 279:                                                      
    ## 280:                                                      
    ##      responseElements.targetHealthDescriptions{}.target.port
    ##   1:                                                        
    ##   2:                                                        
    ##   3:                                                        
    ##   4:                                                        
    ##   5:                                                        
    ##  ---                                                        
    ## 276:                                                        
    ## 277:                                                        
    ## 278:                                                        
    ## 279:                                                        
    ## 280:                                                        
    ##      responseElements.targetHealthDescriptions{}.targetHealth.description
    ##   1:                                                                     
    ##   2:                                                                     
    ##   3:                                                                     
    ##   4:                                                                     
    ##   5:                                                                     
    ##  ---                                                                     
    ## 276:                                                                     
    ## 277:                                                                     
    ## 278:                                                                     
    ## 279:                                                                     
    ## 280:                                                                     
    ##      responseElements.targetHealthDescriptions{}.targetHealth.reason
    ##   1:                                                                
    ##   2:                                                                
    ##   3:                                                                
    ##   4:                                                                
    ##   5:                                                                
    ##  ---                                                                
    ## 276:                                                                
    ## 277:                                                                
    ## 278:                                                                
    ## 279:                                                                
    ## 280:                                                                
    ##      responseElements.targetHealthDescriptions{}.targetHealth.state
    ##   1:                                                               
    ##   2:                                                               
    ##   3:                                                               
    ##   4:                                                               
    ##   5:                                                               
    ##  ---                                                               
    ## 276:                                                               
    ## 277:                                                               
    ## 278:                                                               
    ## 279:                                                               
    ## 280:                                                               
    ##      responseElements.userId
    ##   1:                        
    ##   2:                        
    ##   3:                        
    ##   4:                        
    ##   5:                        
    ##  ---                        
    ## 276:                        
    ## 277:                        
    ## 278:                        
    ## 279:                        
    ## 280:                        
    ##                                                                                                                                                                                                                     result
    ##   1: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##   2: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##   3: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##   4: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##   5: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##  ---                                                                                                                                                                                                                      
    ## 276: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ## 277: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ## 278: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ## 279: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ## 280: You have requested more instances (1) than your current instance limit of 0 allows for the specified instance type. Please visit http://aws.amazon.com/contact-us/ec2-request to request an adjustment to this limit.
    ##                         result_id    signature
    ##   1: Client.InstanceLimitExceeded RunInstances
    ##   2: Client.InstanceLimitExceeded RunInstances
    ##   3: Client.InstanceLimitExceeded RunInstances
    ##   4: Client.InstanceLimitExceeded RunInstances
    ##   5: Client.InstanceLimitExceeded RunInstances
    ##  ---                                          
    ## 276: Client.InstanceLimitExceeded RunInstances
    ## 277: Client.InstanceLimitExceeded RunInstances
    ## 278: Client.InstanceLimitExceeded RunInstances
    ## 279: Client.InstanceLimitExceeded RunInstances
    ## 280: Client.InstanceLimitExceeded RunInstances
    ##                                                                                                                                                                     source
    ##   1:           s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/eu-west-1/2018/07/26/622676721278_CloudTrail_eu-west-1_20180726T0525Z_ucdqjIisX1gmpotl.json.gz
    ##   2:           s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/eu-west-1/2018/07/26/622676721278_CloudTrail_eu-west-1_20180726T0525Z_ucdqjIisX1gmpotl.json.gz
    ##   3:           s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/eu-west-1/2018/07/26/622676721278_CloudTrail_eu-west-1_20180726T0525Z_ucdqjIisX1gmpotl.json.gz
    ##   4:           s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/eu-west-1/2018/07/26/622676721278_CloudTrail_eu-west-1_20180726T0525Z_ucdqjIisX1gmpotl.json.gz
    ##   5:           s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/eu-west-1/2018/07/26/622676721278_CloudTrail_eu-west-1_20180726T0525Z_ucdqjIisX1gmpotl.json.gz
    ##  ---                                                                                                                                                                      
    ## 276: s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/ap-northeast-2/2018/07/26/622676721278_CloudTrail_ap-northeast-2_20180726T0520Z_j8h0mj1fNX148yKO.json.gz
    ## 277: s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/ap-northeast-2/2018/07/26/622676721278_CloudTrail_ap-northeast-2_20180726T0520Z_j8h0mj1fNX148yKO.json.gz
    ## 278:           s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/eu-west-2/2018/07/26/622676721278_CloudTrail_eu-west-2_20180726T0525Z_bvzROBU5UyKnFugJ.json.gz
    ## 279:           s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/eu-west-2/2018/07/26/622676721278_CloudTrail_eu-west-2_20180726T0525Z_bvzROBU5UyKnFugJ.json.gz
    ## 280:           s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/eu-west-2/2018/07/26/622676721278_CloudTrail_eu-west-2_20180726T0525Z_bvzROBU5UyKnFugJ.json.gz
    ##      sourceIPAddress     sourcetype   splunk_server splunk_server_group
    ##   1:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ##   2:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ##   3:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ##   4:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ##   5:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ##  ---                                                                   
    ## 276:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ## 277:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ## 278:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ## 279:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ## 280:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ##                 src         src_ip src_user src_user_id src_user_role
    ##   1: 139.198.18.205 139.198.18.205                                 NA
    ##   2: 139.198.18.205 139.198.18.205                                 NA
    ##   3: 139.198.18.205 139.198.18.205                                 NA
    ##   4: 139.198.18.205 139.198.18.205                                 NA
    ##   5: 139.198.18.205 139.198.18.205                                 NA
    ##  ---                                                                 
    ## 276: 139.198.18.205 139.198.18.205                                 NA
    ## 277: 139.198.18.205 139.198.18.205                                 NA
    ## 278: 139.198.18.205 139.198.18.205                                 NA
    ## 279: 139.198.18.205 139.198.18.205                                 NA
    ## 280: 139.198.18.205 139.198.18.205                                 NA
    ##      src_user_type           start_time  status                            tag
    ##   1:            NA 2018-08-20T09:20:58Z failure change\ncloud\nendpoint\nerror
    ##   2:            NA 2018-08-20T09:21:05Z failure change\ncloud\nendpoint\nerror
    ##   3:            NA 2018-08-20T09:20:31Z failure change\ncloud\nendpoint\nerror
    ##   4:            NA 2018-08-20T09:20:33Z failure change\ncloud\nendpoint\nerror
    ##   5:            NA 2018-08-20T09:20:35Z failure change\ncloud\nendpoint\nerror
    ##  ---                                                                          
    ## 276:            NA 2018-08-20T09:18:38Z failure change\ncloud\nendpoint\nerror
    ## 277:            NA 2018-08-20T09:17:24Z failure change\ncloud\nendpoint\nerror
    ## 278:            NA 2018-08-20T09:21:53Z failure change\ncloud\nendpoint\nerror
    ## 279:            NA 2018-08-20T09:21:34Z failure change\ncloud\nendpoint\nerror
    ## 280:            NA 2018-08-20T09:21:58Z failure change\ncloud\nendpoint\nerror
    ##      tag::action tag::app                 tag::eventtype tag::object_category
    ##   1:                   NA change\ncloud\nendpoint\nerror                   NA
    ##   2:                   NA change\ncloud\nendpoint\nerror                   NA
    ##   3:                   NA change\ncloud\nendpoint\nerror                   NA
    ##   4:                   NA change\ncloud\nendpoint\nerror                   NA
    ##   5:                   NA change\ncloud\nendpoint\nerror                   NA
    ##  ---                                                                         
    ## 276:                   NA change\ncloud\nendpoint\nerror                   NA
    ## 277:                   NA change\ncloud\nendpoint\nerror                   NA
    ## 278:                   NA change\ncloud\nendpoint\nerror                   NA
    ## 279:                   NA change\ncloud\nendpoint\nerror                   NA
    ## 280:                   NA change\ncloud\nendpoint\nerror                   NA
    ##      temp_access_key timeendpos timestartpos                  user
    ##   1:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ##   2:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ##   3:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ##   4:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ##   5:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ##  ---                                                              
    ## 276:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ## 277:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ## 278:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ## 279:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ## 280:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ##                                                                userAgent
    ##   1: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   2: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   3: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   4: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   5: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##  ---                                                                    
    ## 276: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 277: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 278: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 279: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 280: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##      userIdentity.accessKeyId userIdentity.accountId
    ##   1:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ##   2:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ##   3:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ##   4:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ##   5:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ##  ---                                                
    ## 276:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ## 277:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ## 278:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ## 279:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ## 280:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ##                              userIdentity.arn userIdentity.invokedBy
    ##   1: arn:aws:iam::622676721278:user/web_admin                       
    ##   2: arn:aws:iam::622676721278:user/web_admin                       
    ##   3: arn:aws:iam::622676721278:user/web_admin                       
    ##   4: arn:aws:iam::622676721278:user/web_admin                       
    ##   5: arn:aws:iam::622676721278:user/web_admin                       
    ##  ---                                                                
    ## 276: arn:aws:iam::622676721278:user/web_admin                       
    ## 277: arn:aws:iam::622676721278:user/web_admin                       
    ## 278: arn:aws:iam::622676721278:user/web_admin                       
    ## 279: arn:aws:iam::622676721278:user/web_admin                       
    ## 280: arn:aws:iam::622676721278:user/web_admin                       
    ##      userIdentity.principalId
    ##   1:    AIDAJNUCQVD57VVGYEFTQ
    ##   2:    AIDAJNUCQVD57VVGYEFTQ
    ##   3:    AIDAJNUCQVD57VVGYEFTQ
    ##   4:    AIDAJNUCQVD57VVGYEFTQ
    ##   5:    AIDAJNUCQVD57VVGYEFTQ
    ##  ---                         
    ## 276:    AIDAJNUCQVD57VVGYEFTQ
    ## 277:    AIDAJNUCQVD57VVGYEFTQ
    ## 278:    AIDAJNUCQVD57VVGYEFTQ
    ## 279:    AIDAJNUCQVD57VVGYEFTQ
    ## 280:    AIDAJNUCQVD57VVGYEFTQ
    ##      userIdentity.sessionContext.attributes.creationDate
    ##   1:                                2018-08-20T09:16:12Z
    ##   2:                                2018-08-20T09:16:12Z
    ##   3:                                2018-08-20T09:16:12Z
    ##   4:                                2018-08-20T09:16:12Z
    ##   5:                                2018-08-20T09:16:12Z
    ##  ---                                                    
    ## 276:                                2018-08-20T09:16:12Z
    ## 277:                                2018-08-20T09:16:12Z
    ## 278:                                2018-08-20T09:16:12Z
    ## 279:                                2018-08-20T09:16:12Z
    ## 280:                                2018-08-20T09:16:12Z
    ##      userIdentity.sessionContext.attributes.mfaAuthenticated userIdentity.type
    ##   1:                                                   FALSE           IAMUser
    ##   2:                                                   FALSE           IAMUser
    ##   3:                                                   FALSE           IAMUser
    ##   4:                                                   FALSE           IAMUser
    ##   5:                                                   FALSE           IAMUser
    ##  ---                                                                          
    ## 276:                                                   FALSE           IAMUser
    ## 277:                                                   FALSE           IAMUser
    ## 278:                                                   FALSE           IAMUser
    ## 279:                                                   FALSE           IAMUser
    ## 280:                                                   FALSE           IAMUser
    ##      userIdentity.userName  userName      user_access_key
    ##   1:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ##   2:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ##   3:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ##   4:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ##   5:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ##  ---                                                     
    ## 276:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ## 277:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ## 278:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ## 279:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ## 280:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ##                                                               user_agent
    ##   1: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   2: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   3: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   4: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   5: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##  ---                                                                    
    ## 276: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 277: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 278: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 279: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 280: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##                                      user_arn user_group_id
    ##   1: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ##   2: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ##   3: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ##   4: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ##   5: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ##  ---                                                       
    ## 276: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ## 277: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ## 278: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ## 279: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ## 280: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ##                    user_id user_role user_type              vendor
    ##   1: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ##   2: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ##   3: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ##   4: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ##   5: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ##  ---                                                              
    ## 276: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ## 277: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ## 278: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ## 279: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ## 280: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ##      vendor_account  vendor_region vpcEndpointId
    ##   1:       6.23e+11      eu-west-1              
    ##   2:       6.23e+11      eu-west-1              
    ##   3:       6.23e+11      eu-west-1              
    ##   4:       6.23e+11      eu-west-1              
    ##   5:       6.23e+11      eu-west-1              
    ##  ---                                            
    ## 276:       6.23e+11 ap-northeast-2              
    ## 277:       6.23e+11 ap-northeast-2              
    ## 278:       6.23e+11      eu-west-2              
    ## 279:       6.23e+11      eu-west-2              
    ## 280:       6.23e+11      eu-west-2

``` r
cloudtrail[errorCode == 'Client.UnauthorizedOperation']
```

    ##                                                 _bkt         _cd
    ##   1: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:2456078
    ##   2: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:2455901
    ##   3: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:2455836
    ##   4: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:2455771
    ##   5: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:2455658
    ##  ---                                                            
    ## 227: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:3166416
    ## 228: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:3166350
    ## 229: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:3166284
    ## 230: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:3166074
    ## 231: botsv3~303~F1874916-CBDC-4E45-BC0A-518E1190B08E 303:3071941
    ##      _eventtype_color _indextime
    ##   1:             none 1534757276
    ##   2:             none 1534757276
    ##   3:             none 1534757276
    ##   4:             none 1534757276
    ##   5:             none 1534757276
    ##  ---                            
    ## 227:             none 1534757708
    ## 228:             none 1534757708
    ## 229:             none 1534757708
    ## 230:             none 1534757708
    ## 231:             none 1534757654
    ##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       _raw
    ##   1:          {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:21:05Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.UnauthorizedOperation"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-4d46d534"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""c3.4xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""e21bfdd7-8b38-4c71-82e2-2893630c560a"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You are not authorized to perform this operation. Encoded authorization failure message: uykWYUN6uvr3OwfLSaCrx4YMob1sBEsT8yeDdgdvkZP7xcMXK6I67bM1N1Vc1xN-WLXd2b7WHEuAeJi88cvw4KHlqJDgxaZtnKOnncASYCfV57N1awT4oyomOm4c6pxpRlVXezUZt4KcBBqc2cQK6n9bfVEv8d8cmYjPaRlJCmNB63iwcQy-nuiCdONOY9WpdB4usRJAl0Z3j7956GfIT8GYKkjk6fGYCpdaBQm2iQpbXE0DE2jNlz3DUaRZpDnw5wqMTM0KaxdNkbDJUGCLYhlfLGiDq5JMox36XNuCfzI5LqPE-SYHXQR3cir-hdHyaCgtJvI91JxhZpepcf6sfi9ZWYF5yFEg_k_Ng2v-xbzTsEflkCMalMyaeg97kaoPJgC5GXDcnopixoJv1N2s-49Z_ot7Yz2wTPxdNc_4ZzceYHQcmS9InxNYQPvYdRS7iS4uHWqUOVC3CZDhxfaOJX26qL5fb4wyVM6pCX0uewXYGozI231M-a0oLOHHi6fdvXOseD6Nu3SO8LNdayxKoT7fAi63bhK9UuLBU6SWahOubvCctQG3PLiP_GkXT5c84Vnkg-3VLPoWWnT5M_CEV49V1_td7Bti7oLbmN4rcmJoLVS3ZaSfZmqp35-DMZpQXlWoee8glQbckUY15C0Wf1ODUqZybmPO_z3fb-U"", ""eventName"": ""RunInstances"", ""requestID"": ""efb4aa67-721a-4498-9de3-dddcbd1cad76"", ""awsRegion"": ""eu-west-1""}
    ##   2:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:20:26Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.UnauthorizedOperation"", ""requestParameters"": {""filterSet"": {}, ""instancesSet"": {}}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""6dab996f-6a2e-4987-9882-015fbbd0eab9"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You are not authorized to perform this operation."", ""eventName"": ""DescribeInstances"", ""requestID"": ""da57718b-3c0d-4c4b-81ee-2ac7d5141b33"", ""awsRegion"": ""eu-west-1""}
    ##   3:           {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:20:52Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.UnauthorizedOperation"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-4d46d534"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""c3.8xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""470ea1d4-9e7d-4aed-b81f-faa89ff3b8df"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You are not authorized to perform this operation. Encoded authorization failure message: soDmUbPRC4O4yAsu0JTVTJNwNsmaZleYXO_6pWpOxnTMqx45nKwgOj2e5XMlZjTtY0IjW1O-m5y6bz3S1PbtlZWa1qeuWnoJO6rN_JxWz3RGMk7ZJXSI97bctGyTRtI_08xye2TbjcUEz8eEBWiF4zjE59zqkiievq1jMZ3LLTtp6KCOyl8Z-RbthZnr7uBi7rfSiYGWJ26bYn7lrCQGdUAWzqjd4xfy8Vzwm6rxzVx2s6jeGAo0O4CfWw2hjfbF6Go3AsyJVnE39GV3OfC1IjMJ4Zlo0xNKlXHtdzP7eVLQZEO5WaFmJqI9WdIRC-JtRTRfJXckN4aqT_jEDwvxCmJr7m99WeZnjvvyQkO4AjerZB-xUQzyynTYPf_l-efeenAPGFCOK1_bdj46gwOrheiT_rRXsJagQK3rx3txrE2EvepXGyMx12GYdqA9SdqOTi2Ch37x7UbpUXPo6wZ4tcz1uPMjiOuFA-OwYLDt-urXSjDt3SrDgWWhpQbRUriYMyW90JjHgw7VmG-rVHEqLo-9dzbq7ua4gVoaQzVbUdy5UuFEClUCqTKQESfXJ0cQtb5_isphm2RNRtO1Bxe4DLJaKDnjQQuJn8rEMmMvWPIh68PkhFLNw8fjXoZg9BAECAvgNEfBu9qac4gHdFq-W-D1KylHYVxdBRhvcA"", ""eventName"": ""RunInstances"", ""requestID"": ""47608c96-c373-4b50-a01b-e2fb67126b58"", ""awsRegion"": ""eu-west-1""}
    ##   4:          {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:20:53Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.UnauthorizedOperation"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-4d46d534"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""r3.8xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""13a05f52-c939-46a9-a6f0-5c25405fd65d"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You are not authorized to perform this operation. Encoded authorization failure message: V8oNUk1OFBOj_y6MC-ZFHiHGltuaCn7-Oejei6g9cSshkFnOREh-iZMO3EK2deoKvzRDdWS4GC5oH8CDKpJjdQ9RMjzBpUrGPzu-CJsdhsJp9XZklx3TOjykmTLhDakW656yb-6AjCY5U65eC_PYhM8JPE2l45HM1sf8j4xrcTSSO_uzeMw-YOncc4DDQx2c3HYM-PZTFeiuwiK2hn-8hFXvVDJlVkP2AWg3t6kLPz8e6ZY_f6uJjzGcXj-8bLwAvTlXqTjDvsSlKlQcFvbVNx13mRvu5GV66ftp8deeSNdREel9qG-p27fMMDgF-YQTMCFflbpIYDENuEIiAuqQGgApSMLrMVMSz9T7zAfEp7IYTlq2a3OjExHrY-kGIfDrmFTrwCKt__b1UywSEot_agf_IFCuEabMzT9wSRIu710MjIz8M0gtHs4wP9kPlHo3a5gDc60YvFURBBd11S2grcelgog36ER9tlf7HvaBHkZWfHxiJneVj34SLHKta1fAGHuaUGCrkkMk45aar7cVv62aStnM6B_mizg4sgBLEC3M_2lFOAIphvHW4ApgLymLtBPdsiGhbQCIRXiNnIYpPGJFKP-evgzAfFBvDt53tDS4kkZvLdh38j-FfhX0h2viQxenEHmsr8zF6jP3LTQPow6lZIcdFHjMMyCjPAs"", ""eventName"": ""RunInstances"", ""requestID"": ""4d42a81f-8b8b-4f3a-91c5-c1a1a8951800"", ""awsRegion"": ""eu-west-1""}
    ##   5:           {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:21:01Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.UnauthorizedOperation"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-4d46d534"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""c4.4xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""c4cf950c-f337-4e48-8587-2d451a01b58e"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You are not authorized to perform this operation. Encoded authorization failure message: sIgNW6SqXz3GgKO7OabL1ieLKRRw_0jjaLtx_JDQiV7TzfaGp0brOE4_RMJl8helfJWu1q95ZYja0xKyohvfF6cjeYqAvZExq069pkuQKREiFrmDQYaHTThINsGfYfRGzVY4VcCbbx99xjXgXIxH1Zu0-y_-gpHrb4_dESwhUCrJKExLA4ddHb_JqmgHtRJj5UGaTlLFYYh_DIF_dVHV5syrgEPYlXFvnypF5XtE9QIY-xZHUCft_BG3NKUPNCtEOoPNK0Wi9Vg9Jn_ty4TdYJiGt5nxULMYvkiQHrCiLZqHEqVjAEqNNDt2W8FTto48WLS09PB3-mQBUi3DnltrVt4IfEwaumDloPbVlkSTBQcMnaNTFTov6LY4whwVxdPy4o6aQsQiIiUH3IZsEBVtZhl9Q-5Xn0jGqnRFHlRY0iMKijON6SAXPvRDjk9WyW4S6aIa6X03W1ON8ZN4sYXCstZLCkcydKsR3Tsapiv6v-NUPA4bFtn6w29aEWCUW_e5GPa17qsKrQwjhZnVL8-ZdZNwU9PppQTz0EQrngcBRmDfbzPU9_Z2tXFClZj9SqARaR2rVnR4siGwc6Fvyu_47OUaUoNV1H22igD-sNmhzKmlw_Rg-4z5pDizbUAFIm3kHK5zYMBPUQXoQhnB-3DoQcBhrbaO4KhcEVx0Ug"", ""eventName"": ""RunInstances"", ""requestID"": ""4a13a9d1-68eb-4880-a4ab-55e467ed32f3"", ""awsRegion"": ""eu-west-1""}
    ##  ---                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
    ## 227: {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:18:40Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.UnauthorizedOperation"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-67973709"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""c4.2xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""fda7159f-c22b-4728-b881-8e256d6b07e9"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You are not authorized to perform this operation. Encoded authorization failure message: sFso9_AhbnX87-4WNPO-4L46kGsRRl6ejlV5PfeDA8K0QQXYMPEfXWeDJLITI9xAPvtmEKd8dDyGk2iEhAruo7GoTbTkUBRXkeqVtU9wvVE_HQaXMFdGX1FOdw6ff9KnCZrLNJOHCmnV_tQnt4V4HhewieshNc3URQ6-jvNMYjTztb9cp8vrE9tjNIkz5j47XN4FR3F-26qPHNgOW582_nYOSv-R1sEQUe6QAcUMaTuMPUVw8pU2xePiAPjs8s9G3ycxyZI3pMXDBXTCP4v1Tu6VR-q0iF9DUG8PBk5vB9_VSH7RUiw9HVfoulhSOx6KIms71VxzmURHKFx2imUUFIgTduBXFfDZV8GGr1diVW8_CDqWqXgIbh-jzDeafYtO66KYSGoGZ-zQlHbHuNo0qFW0_m0geqhdr5LUwgPsDnp_CO_HwFX1ZoWawKYq748peb22SfdWsf-CFRaFOvaZoQjOrCX34aJoO4gKaz0UA-pht4-a7rfxYUJcFzbnXrOOZkOzek0vl3_vMh4hdWRa21rv6j5IFw63HAXA-B6VII93oLO-7pUNBoRnQgnnzKeRL2i_ZpNg5RGfe3DipPVrzKCmjaQnVpPKQCkZs7JdpX8GPvDwcEEVZ1MOdHrX62HGR85SbkB05BorOpcKV8d8kHf7iP7P2tEr80IQsqFjglY"", ""eventName"": ""RunInstances"", ""requestID"": ""88b73548-211e-4491-b8e0-19513a172630"", ""awsRegion"": ""ap-northeast-2""}
    ## 228: {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:18:43Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.UnauthorizedOperation"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-67973709"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""m4.2xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""29b2e7c8-bd15-4e93-92a5-50bb8d2c20eb"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You are not authorized to perform this operation. Encoded authorization failure message: xvZitPBwgPLNwD7syX4l0-Mv3UqLCQleg116nNGCQmXs7g6PcZh3_uGypCE2FiryY-tH1dMTQd31kpWiW3VgJm4XQT_Mhp7hbbsRrDSqp3LnbKxFZy8INHqZ_20Wa_CvsB4I5Jlit1fSvynfwTdXD158hUpkDd7765L2bYO0j5U81D6qRfn7FG5yuLM3sB9Gk9SCQpCohYWT2piA0TUCqGXQ1TjqG5sCsxOnb5ekBUDk5pXB2cLpvw-04gK7Ovbaf1PY8c0zNY9MdyaK9u68gsljBlMyIJMpdF1TqfcIm6e-gQGnbBHnJvFUW1k7D98YhJc2OBO12oRQ7mcsUwm_zqlhFOsujif0-AYthNECskAIx9Pf-Yr1uCgi1wcIZn88zaT-DP-Osrlm5E3uyZPyw9jq-fZ3SgjWGzzKN0A5B83WbpFj_4F71Y6z-fBuDomyYMAgCcU9gChN2-OX1PGJcY7rNWx7Hs39yxNL5s8tuYsttOA7cSsmoPoCnfuH7Ccvy2KH4BaB8Ea0HqTaCr1Negz7PxqpxJnnJd_LJCc5REElC4U2QRD9YAFCtMaCN2BHDd3lswb0i4U2Lp32ypEzpuY8rVXrROrSSTXg3tXzjvLAd8ZU5JueR346hHJ8y3KKekABK7MiD6BbvDvyttHFM1r0W2fs3Kf5xEqP-716LyI"", ""eventName"": ""RunInstances"", ""requestID"": ""a2648809-b914-4465-aaa1-de79b08d8067"", ""awsRegion"": ""ap-northeast-2""}
    ## 229:  {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:18:44Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.UnauthorizedOperation"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-67973709"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""t2.2xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""5a09005e-2d47-4cb8-9a36-4f500a557f45"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You are not authorized to perform this operation. Encoded authorization failure message: WkaNGddTeVqgAOdofQBkATAnLtD1czbdXR-MExrUIAezlLVXv8J1Hf_Zi5HO4HmHL77UMeMDgw9-7MoymK-2VzdGW8EB_X8iMhLWYw-6KqDi_n2iumaEvNBA2a9fbUJdoNhUPe88fzU3zhHNJlggYcTMNZOrg1tnkwQAM5aEzoewlRCa8mEcy36HUUed9UxBgQclsibd0V5uNr1garIGoUhQ-yJ_xSXVI51rH7jLpAiUDQlk82dMuIf6cQVwFjpapVqeWS23PF9WnL6eA6lm7W-4FfcPh2sEPDD61V4O8D8a9OMtVkBoYk1ahh7v1Eb-KuMA-k5buyX-unFtkt49qkZOe4bxfEcdxlj_wBleAaay3vgvyYFIptOw02slofRiPufe1wQZGwLPV-KIUnjdUiJ9PPL7-lwAGQL9I1nTKtAQa8wS6K6gV8anOEbkRS3CZJsOxhc8ZZ6Ukr3PLTkSJs9lbrDp76XKblebgi_vNZHpntDKIhtRQs5JOmE3ZONaC-1OHX0e5C5jz_5UxYBx0qqZ3AOc6sPOE45TIjpMLYkERlRovuIx8UHxYczHUUiZD1DdC9h0Is3qv3OhZRfiPVc3XIOykCQ5PNGFz-ej5qkWTancwRX_eKjlmjHnpyevR6CozU7ct4fhVDn1vku7UzwtAOBAhon1OJlUouvtOg"", ""eventName"": ""RunInstances"", ""requestID"": ""1d39afea-80fe-4a3c-b578-fa597ec525d6"", ""awsRegion"": ""ap-northeast-2""}
    ## 230: {""sourceIPAddress"": ""139.198.18.205"", ""eventTime"": ""2018-08-20T09:17:48Z"", ""userAgent"": ""Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.UnauthorizedOperation"", ""requestParameters"": {""disableApiTermination"": true, ""monitoring"": {""enabled"": false}, ""tagSpecificationSet"": {""items"": [{""resourceType"": ""instance"", ""tags"": [{""key"": ""my_i_key"", ""value"": ""my_i_val""}]}]}, ""userData"": ""<sensitiveDataRemoved>"", ""instancesSet"": {""items"": [{""imageId"": ""ami-67973709"", ""minCount"": 1, ""maxCount"": 10}]}, ""blockDeviceMapping"": {}, ""instanceType"": ""c4.8xlarge""}, ""userIdentity"": {""sessionContext"": {""attributes"": {""mfaAuthenticated"": ""false"", ""creationDate"": ""2018-08-20T09:16:12Z""}}, ""accessKeyId"": ""ASIAZB6TMXZ7LL6JBJQA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""d961383a-3875-4be0-98eb-944296d06938"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You are not authorized to perform this operation. Encoded authorization failure message: 3lDHOCCsUvr52KUDdk74MpoxaHTr5rOX6Cwb3k7ZbWtA0RsMyARKNK8JAP-7FIx6nzGcDeeMG8Eei5YUbbdKkLdNAvEClAon0qkvOQbr4ofJnjBFsxlQegvg-mo0kQ2YCneyVw-kj4A4E4dUby_zUPyVLyb1_PWTg-OmyMBE3X6V2scEEOrjS0S_7Xk7-2LUbLFH4lgeRn1qAED_MPiSRCmBcKo_SRJ90BC4oB_C6uKTchWl2ZhCitFucYwZBlTTtK7G9rBXj7jyEvIz0QSNwYXW4b4eaTv4nVbI2vN80odXID0HhRSbn-RujsE_B2P_zy4xvWkGZdNiG--PgT54vi0ijIfDkbdfmbsDetJJL4J1_pTkWU7vMV_9XKetFiniorBgzf7tDx8CbCPQWs-0ro0V-rSqIvP7nA341aSkzDRdpP45rno2EzSfwhg7IzsnHbfZ6mzeM50SdHbsl4vnGZEZxsJwgA8OQU-4a4vI4k3sa7bS_SSLva3xRXhIiO4yo7VMvJcoI7SsmKYlj3BI8pWh5UcE2ZzA1DYGmEisYxhb0wTQ_TR17h3WC4MaZRFpZ47Uz1bDA4tidtDvDiaLTwNW1cJGwugThWQ-9QEF-zIzNq6Cz7eNehAqPAZuAQXyg3-8ZijyIp2FSeCbxZ7afEsRmGxL26AmPwPF7egmxaY"", ""eventName"": ""RunInstances"", ""requestID"": ""7e66d8dd-f28e-49ba-9624-ceffb76ad8bb"", ""awsRegion"": ""ap-northeast-2""}
    ## 231:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            {""sourceIPAddress"": ""82.102.18.111"", ""eventTime"": ""2018-08-20T09:27:06Z"", ""userAgent"": ""ElasticWolf/5.1.6"", ""responseElements"": null, ""eventSource"": ""ec2.amazonaws.com"", ""eventType"": ""AwsApiCall"", ""errorCode"": ""Client.UnauthorizedOperation"", ""requestParameters"": {""filterSet"": {}, ""accountAttributeNameSet"": {}}, ""userIdentity"": {""accessKeyId"": ""AKIAJOGCDXJ5NW5PXUPA"", ""type"": ""IAMUser"", ""userName"": ""web_admin"", ""accountId"": ""622676721278"", ""arn"": ""arn:aws:iam::622676721278:user/web_admin"", ""principalId"": ""AIDAJNUCQVD57VVGYEFTQ""}, ""eventID"": ""c077df0d-2435-4152-9127-09e579dd1fb2"", ""eventVersion"": ""1.05"", ""recipientAccountId"": ""622676721278"", ""errorMessage"": ""You are not authorized to perform this operation."", ""eventName"": ""DescribeAccountAttributes"", ""requestID"": ""f94dfb04-2d7b-40a8-b3cc-3664b9463db8"", ""awsRegion"": ""us-east-1""}
    ##         _sourcetype      _time  action additionalEventData.LoginTo
    ##   1: aws:cloudtrail 1534756865 created                            
    ##   2: aws:cloudtrail 1534756826                                    
    ##   3: aws:cloudtrail 1534756852 created                            
    ##   4: aws:cloudtrail 1534756853 created                            
    ##   5: aws:cloudtrail 1534756861 created                            
    ##  ---                                                              
    ## 227: aws:cloudtrail 1534756720 created                            
    ## 228: aws:cloudtrail 1534756723 created                            
    ## 229: aws:cloudtrail 1534756724 created                            
    ## 230: aws:cloudtrail 1534756668 created                            
    ## 231: aws:cloudtrail 1534757226                                    
    ##      additionalEventData.MFAUsed additionalEventData.MobileVersion
    ##   1:                                                              
    ##   2:                                                              
    ##   3:                                                              
    ##   4:                                                              
    ##   5:                                                              
    ##  ---                                                              
    ## 227:                                                              
    ## 228:                                                              
    ## 229:                                                              
    ## 230:                                                              
    ## 231:                                                              
    ##      additionalEventData.vpcEndpointId apiVersion               app
    ##   1:                                              ec2.amazonaws.com
    ##   2:                                              ec2.amazonaws.com
    ##   3:                                              ec2.amazonaws.com
    ##   4:                                              ec2.amazonaws.com
    ##   5:                                              ec2.amazonaws.com
    ##  ---                                                               
    ## 227:                                              ec2.amazonaws.com
    ## 228:                                              ec2.amazonaws.com
    ## 229:                                              ec2.amazonaws.com
    ## 230:                                              ec2.amazonaws.com
    ## 231:                                              ec2.amazonaws.com
    ##      authentication_method      awsRegion aws_account_id change_type
    ##   1:                            eu-west-1       6.23e+11         EC2
    ##   2:                            eu-west-1       6.23e+11         EC2
    ##   3:                            eu-west-1       6.23e+11         EC2
    ##   4:                            eu-west-1       6.23e+11         EC2
    ##   5:                            eu-west-1       6.23e+11         EC2
    ##  ---                                                                
    ## 227:                       ap-northeast-2       6.23e+11         EC2
    ## 228:                       ap-northeast-2       6.23e+11         EC2
    ## 229:                       ap-northeast-2       6.23e+11         EC2
    ## 230:                       ap-northeast-2       6.23e+11         EC2
    ## 231:                            us-east-1       6.23e+11         EC2
    ##                        command date_hour date_mday date_minute date_month
    ##   1:              RunInstances         9        20          27     august
    ##   2:         DescribeInstances         9        20          27     august
    ##   3:              RunInstances         9        20          27     august
    ##   4:              RunInstances         9        20          27     august
    ##   5:              RunInstances         9        20          27     august
    ##  ---                                                                     
    ## 227:              RunInstances         9        20          35     august
    ## 228:              RunInstances         9        20          35     august
    ## 229:              RunInstances         9        20          35     august
    ## 230:              RunInstances         9        20          35     august
    ## 231: DescribeAccountAttributes         9        20          34     august
    ##      date_second date_wday date_year date_zone desc              dest
    ##   1:          56    monday      2018         0                       
    ##   2:          56    monday      2018         0                       
    ##   3:          56    monday      2018         0                       
    ##   4:          56    monday      2018         0                       
    ##   5:          56    monday      2018         0                       
    ##  ---                                                                 
    ## 227:           8    monday      2018         0                       
    ## 228:           8    monday      2018         0                       
    ## 229:           8    monday      2018         0                       
    ## 230:           8    monday      2018         0                       
    ## 231:          14    monday      2018         0      ec2.amazonaws.com
    ##                    dvc                    errorCode
    ##   1: ec2.amazonaws.com Client.UnauthorizedOperation
    ##   2: ec2.amazonaws.com Client.UnauthorizedOperation
    ##   3: ec2.amazonaws.com Client.UnauthorizedOperation
    ##   4: ec2.amazonaws.com Client.UnauthorizedOperation
    ##   5: ec2.amazonaws.com Client.UnauthorizedOperation
    ##  ---                                               
    ## 227: ec2.amazonaws.com Client.UnauthorizedOperation
    ## 228: ec2.amazonaws.com Client.UnauthorizedOperation
    ## 229: ec2.amazonaws.com Client.UnauthorizedOperation
    ## 230: ec2.amazonaws.com Client.UnauthorizedOperation
    ## 231: ec2.amazonaws.com Client.UnauthorizedOperation
    ##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              errorMessage
    ##   1:     You are not authorized to perform this operation. Encoded authorization failure message: uykWYUN6uvr3OwfLSaCrx4YMob1sBEsT8yeDdgdvkZP7xcMXK6I67bM1N1Vc1xN-WLXd2b7WHEuAeJi88cvw4KHlqJDgxaZtnKOnncASYCfV57N1awT4oyomOm4c6pxpRlVXezUZt4KcBBqc2cQK6n9bfVEv8d8cmYjPaRlJCmNB63iwcQy-nuiCdONOY9WpdB4usRJAl0Z3j7956GfIT8GYKkjk6fGYCpdaBQm2iQpbXE0DE2jNlz3DUaRZpDnw5wqMTM0KaxdNkbDJUGCLYhlfLGiDq5JMox36XNuCfzI5LqPE-SYHXQR3cir-hdHyaCgtJvI91JxhZpepcf6sfi9ZWYF5yFEg_k_Ng2v-xbzTsEflkCMalMyaeg97kaoPJgC5GXDcnopixoJv1N2s-49Z_ot7Yz2wTPxdNc_4ZzceYHQcmS9InxNYQPvYdRS7iS4uHWqUOVC3CZDhxfaOJX26qL5fb4wyVM6pCX0uewXYGozI231M-a0oLOHHi6fdvXOseD6Nu3SO8LNdayxKoT7fAi63bhK9UuLBU6SWahOubvCctQG3PLiP_GkXT5c84Vnkg-3VLPoWWnT5M_CEV49V1_td7Bti7oLbmN4rcmJoLVS3ZaSfZmqp35-DMZpQXlWoee8glQbckUY15C0Wf1ODUqZybmPO_z3fb-U
    ##   2:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    You are not authorized to perform this operation.
    ##   3:      You are not authorized to perform this operation. Encoded authorization failure message: soDmUbPRC4O4yAsu0JTVTJNwNsmaZleYXO_6pWpOxnTMqx45nKwgOj2e5XMlZjTtY0IjW1O-m5y6bz3S1PbtlZWa1qeuWnoJO6rN_JxWz3RGMk7ZJXSI97bctGyTRtI_08xye2TbjcUEz8eEBWiF4zjE59zqkiievq1jMZ3LLTtp6KCOyl8Z-RbthZnr7uBi7rfSiYGWJ26bYn7lrCQGdUAWzqjd4xfy8Vzwm6rxzVx2s6jeGAo0O4CfWw2hjfbF6Go3AsyJVnE39GV3OfC1IjMJ4Zlo0xNKlXHtdzP7eVLQZEO5WaFmJqI9WdIRC-JtRTRfJXckN4aqT_jEDwvxCmJr7m99WeZnjvvyQkO4AjerZB-xUQzyynTYPf_l-efeenAPGFCOK1_bdj46gwOrheiT_rRXsJagQK3rx3txrE2EvepXGyMx12GYdqA9SdqOTi2Ch37x7UbpUXPo6wZ4tcz1uPMjiOuFA-OwYLDt-urXSjDt3SrDgWWhpQbRUriYMyW90JjHgw7VmG-rVHEqLo-9dzbq7ua4gVoaQzVbUdy5UuFEClUCqTKQESfXJ0cQtb5_isphm2RNRtO1Bxe4DLJaKDnjQQuJn8rEMmMvWPIh68PkhFLNw8fjXoZg9BAECAvgNEfBu9qac4gHdFq-W-D1KylHYVxdBRhvcA
    ##   4:     You are not authorized to perform this operation. Encoded authorization failure message: V8oNUk1OFBOj_y6MC-ZFHiHGltuaCn7-Oejei6g9cSshkFnOREh-iZMO3EK2deoKvzRDdWS4GC5oH8CDKpJjdQ9RMjzBpUrGPzu-CJsdhsJp9XZklx3TOjykmTLhDakW656yb-6AjCY5U65eC_PYhM8JPE2l45HM1sf8j4xrcTSSO_uzeMw-YOncc4DDQx2c3HYM-PZTFeiuwiK2hn-8hFXvVDJlVkP2AWg3t6kLPz8e6ZY_f6uJjzGcXj-8bLwAvTlXqTjDvsSlKlQcFvbVNx13mRvu5GV66ftp8deeSNdREel9qG-p27fMMDgF-YQTMCFflbpIYDENuEIiAuqQGgApSMLrMVMSz9T7zAfEp7IYTlq2a3OjExHrY-kGIfDrmFTrwCKt__b1UywSEot_agf_IFCuEabMzT9wSRIu710MjIz8M0gtHs4wP9kPlHo3a5gDc60YvFURBBd11S2grcelgog36ER9tlf7HvaBHkZWfHxiJneVj34SLHKta1fAGHuaUGCrkkMk45aar7cVv62aStnM6B_mizg4sgBLEC3M_2lFOAIphvHW4ApgLymLtBPdsiGhbQCIRXiNnIYpPGJFKP-evgzAfFBvDt53tDS4kkZvLdh38j-FfhX0h2viQxenEHmsr8zF6jP3LTQPow6lZIcdFHjMMyCjPAs
    ##   5:      You are not authorized to perform this operation. Encoded authorization failure message: sIgNW6SqXz3GgKO7OabL1ieLKRRw_0jjaLtx_JDQiV7TzfaGp0brOE4_RMJl8helfJWu1q95ZYja0xKyohvfF6cjeYqAvZExq069pkuQKREiFrmDQYaHTThINsGfYfRGzVY4VcCbbx99xjXgXIxH1Zu0-y_-gpHrb4_dESwhUCrJKExLA4ddHb_JqmgHtRJj5UGaTlLFYYh_DIF_dVHV5syrgEPYlXFvnypF5XtE9QIY-xZHUCft_BG3NKUPNCtEOoPNK0Wi9Vg9Jn_ty4TdYJiGt5nxULMYvkiQHrCiLZqHEqVjAEqNNDt2W8FTto48WLS09PB3-mQBUi3DnltrVt4IfEwaumDloPbVlkSTBQcMnaNTFTov6LY4whwVxdPy4o6aQsQiIiUH3IZsEBVtZhl9Q-5Xn0jGqnRFHlRY0iMKijON6SAXPvRDjk9WyW4S6aIa6X03W1ON8ZN4sYXCstZLCkcydKsR3Tsapiv6v-NUPA4bFtn6w29aEWCUW_e5GPa17qsKrQwjhZnVL8-ZdZNwU9PppQTz0EQrngcBRmDfbzPU9_Z2tXFClZj9SqARaR2rVnR4siGwc6Fvyu_47OUaUoNV1H22igD-sNmhzKmlw_Rg-4z5pDizbUAFIm3kHK5zYMBPUQXoQhnB-3DoQcBhrbaO4KhcEVx0Ug
    ##  ---                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
    ## 227: You are not authorized to perform this operation. Encoded authorization failure message: sFso9_AhbnX87-4WNPO-4L46kGsRRl6ejlV5PfeDA8K0QQXYMPEfXWeDJLITI9xAPvtmEKd8dDyGk2iEhAruo7GoTbTkUBRXkeqVtU9wvVE_HQaXMFdGX1FOdw6ff9KnCZrLNJOHCmnV_tQnt4V4HhewieshNc3URQ6-jvNMYjTztb9cp8vrE9tjNIkz5j47XN4FR3F-26qPHNgOW582_nYOSv-R1sEQUe6QAcUMaTuMPUVw8pU2xePiAPjs8s9G3ycxyZI3pMXDBXTCP4v1Tu6VR-q0iF9DUG8PBk5vB9_VSH7RUiw9HVfoulhSOx6KIms71VxzmURHKFx2imUUFIgTduBXFfDZV8GGr1diVW8_CDqWqXgIbh-jzDeafYtO66KYSGoGZ-zQlHbHuNo0qFW0_m0geqhdr5LUwgPsDnp_CO_HwFX1ZoWawKYq748peb22SfdWsf-CFRaFOvaZoQjOrCX34aJoO4gKaz0UA-pht4-a7rfxYUJcFzbnXrOOZkOzek0vl3_vMh4hdWRa21rv6j5IFw63HAXA-B6VII93oLO-7pUNBoRnQgnnzKeRL2i_ZpNg5RGfe3DipPVrzKCmjaQnVpPKQCkZs7JdpX8GPvDwcEEVZ1MOdHrX62HGR85SbkB05BorOpcKV8d8kHf7iP7P2tEr80IQsqFjglY
    ## 228: You are not authorized to perform this operation. Encoded authorization failure message: xvZitPBwgPLNwD7syX4l0-Mv3UqLCQleg116nNGCQmXs7g6PcZh3_uGypCE2FiryY-tH1dMTQd31kpWiW3VgJm4XQT_Mhp7hbbsRrDSqp3LnbKxFZy8INHqZ_20Wa_CvsB4I5Jlit1fSvynfwTdXD158hUpkDd7765L2bYO0j5U81D6qRfn7FG5yuLM3sB9Gk9SCQpCohYWT2piA0TUCqGXQ1TjqG5sCsxOnb5ekBUDk5pXB2cLpvw-04gK7Ovbaf1PY8c0zNY9MdyaK9u68gsljBlMyIJMpdF1TqfcIm6e-gQGnbBHnJvFUW1k7D98YhJc2OBO12oRQ7mcsUwm_zqlhFOsujif0-AYthNECskAIx9Pf-Yr1uCgi1wcIZn88zaT-DP-Osrlm5E3uyZPyw9jq-fZ3SgjWGzzKN0A5B83WbpFj_4F71Y6z-fBuDomyYMAgCcU9gChN2-OX1PGJcY7rNWx7Hs39yxNL5s8tuYsttOA7cSsmoPoCnfuH7Ccvy2KH4BaB8Ea0HqTaCr1Negz7PxqpxJnnJd_LJCc5REElC4U2QRD9YAFCtMaCN2BHDd3lswb0i4U2Lp32ypEzpuY8rVXrROrSSTXg3tXzjvLAd8ZU5JueR346hHJ8y3KKekABK7MiD6BbvDvyttHFM1r0W2fs3Kf5xEqP-716LyI
    ## 229:  You are not authorized to perform this operation. Encoded authorization failure message: WkaNGddTeVqgAOdofQBkATAnLtD1czbdXR-MExrUIAezlLVXv8J1Hf_Zi5HO4HmHL77UMeMDgw9-7MoymK-2VzdGW8EB_X8iMhLWYw-6KqDi_n2iumaEvNBA2a9fbUJdoNhUPe88fzU3zhHNJlggYcTMNZOrg1tnkwQAM5aEzoewlRCa8mEcy36HUUed9UxBgQclsibd0V5uNr1garIGoUhQ-yJ_xSXVI51rH7jLpAiUDQlk82dMuIf6cQVwFjpapVqeWS23PF9WnL6eA6lm7W-4FfcPh2sEPDD61V4O8D8a9OMtVkBoYk1ahh7v1Eb-KuMA-k5buyX-unFtkt49qkZOe4bxfEcdxlj_wBleAaay3vgvyYFIptOw02slofRiPufe1wQZGwLPV-KIUnjdUiJ9PPL7-lwAGQL9I1nTKtAQa8wS6K6gV8anOEbkRS3CZJsOxhc8ZZ6Ukr3PLTkSJs9lbrDp76XKblebgi_vNZHpntDKIhtRQs5JOmE3ZONaC-1OHX0e5C5jz_5UxYBx0qqZ3AOc6sPOE45TIjpMLYkERlRovuIx8UHxYczHUUiZD1DdC9h0Is3qv3OhZRfiPVc3XIOykCQ5PNGFz-ej5qkWTancwRX_eKjlmjHnpyevR6CozU7ct4fhVDn1vku7UzwtAOBAhon1OJlUouvtOg
    ## 230: You are not authorized to perform this operation. Encoded authorization failure message: 3lDHOCCsUvr52KUDdk74MpoxaHTr5rOX6Cwb3k7ZbWtA0RsMyARKNK8JAP-7FIx6nzGcDeeMG8Eei5YUbbdKkLdNAvEClAon0qkvOQbr4ofJnjBFsxlQegvg-mo0kQ2YCneyVw-kj4A4E4dUby_zUPyVLyb1_PWTg-OmyMBE3X6V2scEEOrjS0S_7Xk7-2LUbLFH4lgeRn1qAED_MPiSRCmBcKo_SRJ90BC4oB_C6uKTchWl2ZhCitFucYwZBlTTtK7G9rBXj7jyEvIz0QSNwYXW4b4eaTv4nVbI2vN80odXID0HhRSbn-RujsE_B2P_zy4xvWkGZdNiG--PgT54vi0ijIfDkbdfmbsDetJJL4J1_pTkWU7vMV_9XKetFiniorBgzf7tDx8CbCPQWs-0ro0V-rSqIvP7nA341aSkzDRdpP45rno2EzSfwhg7IzsnHbfZ6mzeM50SdHbsl4vnGZEZxsJwgA8OQU-4a4vI4k3sa7bS_SSLva3xRXhIiO4yo7VMvJcoI7SsmKYlj3BI8pWh5UcE2ZzA1DYGmEisYxhb0wTQ_TR17h3WC4MaZRFpZ47Uz1bDA4tidtDvDiaLTwNW1cJGwugThWQ-9QEF-zIzNq6Cz7eNehAqPAZuAQXyg3-8ZijyIp2FSeCbxZ7afEsRmGxL26AmPwPF7egmxaY
    ## 231:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    You are not authorized to perform this operation.
    ##                                   eventID                 eventName
    ##   1: e21bfdd7-8b38-4c71-82e2-2893630c560a              RunInstances
    ##   2: 6dab996f-6a2e-4987-9882-015fbbd0eab9         DescribeInstances
    ##   3: 470ea1d4-9e7d-4aed-b81f-faa89ff3b8df              RunInstances
    ##   4: 13a05f52-c939-46a9-a6f0-5c25405fd65d              RunInstances
    ##   5: c4cf950c-f337-4e48-8587-2d451a01b58e              RunInstances
    ##  ---                                                               
    ## 227: fda7159f-c22b-4728-b881-8e256d6b07e9              RunInstances
    ## 228: 29b2e7c8-bd15-4e93-92a5-50bb8d2c20eb              RunInstances
    ## 229: 5a09005e-2d47-4cb8-9a36-4f500a557f45              RunInstances
    ## 230: d961383a-3875-4be0-98eb-944296d06938              RunInstances
    ## 231: c077df0d-2435-4152-9127-09e579dd1fb2 DescribeAccountAttributes
    ##            eventSource            eventTime  eventType eventVersion
    ##   1: ec2.amazonaws.com 2018-08-20T09:21:05Z AwsApiCall         1.05
    ##   2: ec2.amazonaws.com 2018-08-20T09:20:26Z AwsApiCall         1.05
    ##   3: ec2.amazonaws.com 2018-08-20T09:20:52Z AwsApiCall         1.05
    ##   4: ec2.amazonaws.com 2018-08-20T09:20:53Z AwsApiCall         1.05
    ##   5: ec2.amazonaws.com 2018-08-20T09:21:01Z AwsApiCall         1.05
    ##  ---                                                               
    ## 227: ec2.amazonaws.com 2018-08-20T09:18:40Z AwsApiCall         1.05
    ## 228: ec2.amazonaws.com 2018-08-20T09:18:43Z AwsApiCall         1.05
    ## 229: ec2.amazonaws.com 2018-08-20T09:18:44Z AwsApiCall         1.05
    ## 230: ec2.amazonaws.com 2018-08-20T09:17:48Z AwsApiCall         1.05
    ## 231: ec2.amazonaws.com 2018-08-20T09:27:06Z AwsApiCall         1.05
    ##                                                                                          eventtype
    ##   1: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors err0r nix_errors
    ##   2:                                                 aws_cloudtrail_acctmgmt aws_cloudtrail_errors
    ##   3: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors err0r nix_errors
    ##   4: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors err0r nix_errors
    ##   5: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors err0r nix_errors
    ##  ---                                                                                              
    ## 227: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors err0r nix_errors
    ## 228: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors err0r nix_errors
    ## 229: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors err0r nix_errors
    ## 230: aws_cloudtrail_delete_events aws_cloudtrail_ec2_events aws_cloudtrail_errors err0r nix_errors
    ## 231:                                                 aws_cloudtrail_acctmgmt aws_cloudtrail_errors
    ##                 host  index linecount                          msg object
    ##   1: splunk.froth.ly botsv3         1 Client.UnauthorizedOperation       
    ##   2: splunk.froth.ly botsv3         1 Client.UnauthorizedOperation       
    ##   3: splunk.froth.ly botsv3         1 Client.UnauthorizedOperation       
    ##   4: splunk.froth.ly botsv3         1 Client.UnauthorizedOperation       
    ##   5: splunk.froth.ly botsv3         1 Client.UnauthorizedOperation       
    ##  ---                                                                     
    ## 227: splunk.froth.ly botsv3         1 Client.UnauthorizedOperation       
    ## 228: splunk.froth.ly botsv3         1 Client.UnauthorizedOperation       
    ## 229: splunk.froth.ly botsv3         1 Client.UnauthorizedOperation       
    ## 230: splunk.froth.ly botsv3         1 Client.UnauthorizedOperation       
    ## 231: splunk.froth.ly botsv3         1 Client.UnauthorizedOperation       
    ##      object_category object_id    product
    ##   1:        instance           CloudTrail
    ##   2:         unknown           CloudTrail
    ##   3:        instance           CloudTrail
    ##   4:        instance           CloudTrail
    ##   5:        instance           CloudTrail
    ##  ---                                     
    ## 227:        instance           CloudTrail
    ## 228:        instance           CloudTrail
    ## 229:        instance           CloudTrail
    ## 230:        instance           CloudTrail
    ## 231:         unknown           CloudTrail
    ##                                                                     punct
    ##   1:      {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""
    ##   2:      {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""
    ##   3:      {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""
    ##   4:      {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""
    ##   5:      {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""
    ##  ---                                                                     
    ## 227:      {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""
    ## 228:      {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""
    ## 229:      {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""
    ## 230:      {"""":_""..."",_"""":_""--::"",_"""":_""/.._/.._/..--_/.."",_""
    ## 231: {"""":_""..."",_"""":_""--::"",_"""":_""/.."",_"""":_,_"""":_"".."",
    ##      readOnly
    ##   1:       NA
    ##   2:       NA
    ##   3:       NA
    ##   4:       NA
    ##   5:       NA
    ##  ---         
    ## 227:       NA
    ## 228:       NA
    ## 229:       NA
    ## 230:       NA
    ## 231:       NA
    ##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    reason
    ##   1:     You are not authorized to perform this operation. Encoded authorization failure message: uykWYUN6uvr3OwfLSaCrx4YMob1sBEsT8yeDdgdvkZP7xcMXK6I67bM1N1Vc1xN-WLXd2b7WHEuAeJi88cvw4KHlqJDgxaZtnKOnncASYCfV57N1awT4oyomOm4c6pxpRlVXezUZt4KcBBqc2cQK6n9bfVEv8d8cmYjPaRlJCmNB63iwcQy-nuiCdONOY9WpdB4usRJAl0Z3j7956GfIT8GYKkjk6fGYCpdaBQm2iQpbXE0DE2jNlz3DUaRZpDnw5wqMTM0KaxdNkbDJUGCLYhlfLGiDq5JMox36XNuCfzI5LqPE-SYHXQR3cir-hdHyaCgtJvI91JxhZpepcf6sfi9ZWYF5yFEg_k_Ng2v-xbzTsEflkCMalMyaeg97kaoPJgC5GXDcnopixoJv1N2s-49Z_ot7Yz2wTPxdNc_4ZzceYHQcmS9InxNYQPvYdRS7iS4uHWqUOVC3CZDhxfaOJX26qL5fb4wyVM6pCX0uewXYGozI231M-a0oLOHHi6fdvXOseD6Nu3SO8LNdayxKoT7fAi63bhK9UuLBU6SWahOubvCctQG3PLiP_GkXT5c84Vnkg-3VLPoWWnT5M_CEV49V1_td7Bti7oLbmN4rcmJoLVS3ZaSfZmqp35-DMZpQXlWoee8glQbckUY15C0Wf1ODUqZybmPO_z3fb-U
    ##   2:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    You are not authorized to perform this operation.
    ##   3:      You are not authorized to perform this operation. Encoded authorization failure message: soDmUbPRC4O4yAsu0JTVTJNwNsmaZleYXO_6pWpOxnTMqx45nKwgOj2e5XMlZjTtY0IjW1O-m5y6bz3S1PbtlZWa1qeuWnoJO6rN_JxWz3RGMk7ZJXSI97bctGyTRtI_08xye2TbjcUEz8eEBWiF4zjE59zqkiievq1jMZ3LLTtp6KCOyl8Z-RbthZnr7uBi7rfSiYGWJ26bYn7lrCQGdUAWzqjd4xfy8Vzwm6rxzVx2s6jeGAo0O4CfWw2hjfbF6Go3AsyJVnE39GV3OfC1IjMJ4Zlo0xNKlXHtdzP7eVLQZEO5WaFmJqI9WdIRC-JtRTRfJXckN4aqT_jEDwvxCmJr7m99WeZnjvvyQkO4AjerZB-xUQzyynTYPf_l-efeenAPGFCOK1_bdj46gwOrheiT_rRXsJagQK3rx3txrE2EvepXGyMx12GYdqA9SdqOTi2Ch37x7UbpUXPo6wZ4tcz1uPMjiOuFA-OwYLDt-urXSjDt3SrDgWWhpQbRUriYMyW90JjHgw7VmG-rVHEqLo-9dzbq7ua4gVoaQzVbUdy5UuFEClUCqTKQESfXJ0cQtb5_isphm2RNRtO1Bxe4DLJaKDnjQQuJn8rEMmMvWPIh68PkhFLNw8fjXoZg9BAECAvgNEfBu9qac4gHdFq-W-D1KylHYVxdBRhvcA
    ##   4:     You are not authorized to perform this operation. Encoded authorization failure message: V8oNUk1OFBOj_y6MC-ZFHiHGltuaCn7-Oejei6g9cSshkFnOREh-iZMO3EK2deoKvzRDdWS4GC5oH8CDKpJjdQ9RMjzBpUrGPzu-CJsdhsJp9XZklx3TOjykmTLhDakW656yb-6AjCY5U65eC_PYhM8JPE2l45HM1sf8j4xrcTSSO_uzeMw-YOncc4DDQx2c3HYM-PZTFeiuwiK2hn-8hFXvVDJlVkP2AWg3t6kLPz8e6ZY_f6uJjzGcXj-8bLwAvTlXqTjDvsSlKlQcFvbVNx13mRvu5GV66ftp8deeSNdREel9qG-p27fMMDgF-YQTMCFflbpIYDENuEIiAuqQGgApSMLrMVMSz9T7zAfEp7IYTlq2a3OjExHrY-kGIfDrmFTrwCKt__b1UywSEot_agf_IFCuEabMzT9wSRIu710MjIz8M0gtHs4wP9kPlHo3a5gDc60YvFURBBd11S2grcelgog36ER9tlf7HvaBHkZWfHxiJneVj34SLHKta1fAGHuaUGCrkkMk45aar7cVv62aStnM6B_mizg4sgBLEC3M_2lFOAIphvHW4ApgLymLtBPdsiGhbQCIRXiNnIYpPGJFKP-evgzAfFBvDt53tDS4kkZvLdh38j-FfhX0h2viQxenEHmsr8zF6jP3LTQPow6lZIcdFHjMMyCjPAs
    ##   5:      You are not authorized to perform this operation. Encoded authorization failure message: sIgNW6SqXz3GgKO7OabL1ieLKRRw_0jjaLtx_JDQiV7TzfaGp0brOE4_RMJl8helfJWu1q95ZYja0xKyohvfF6cjeYqAvZExq069pkuQKREiFrmDQYaHTThINsGfYfRGzVY4VcCbbx99xjXgXIxH1Zu0-y_-gpHrb4_dESwhUCrJKExLA4ddHb_JqmgHtRJj5UGaTlLFYYh_DIF_dVHV5syrgEPYlXFvnypF5XtE9QIY-xZHUCft_BG3NKUPNCtEOoPNK0Wi9Vg9Jn_ty4TdYJiGt5nxULMYvkiQHrCiLZqHEqVjAEqNNDt2W8FTto48WLS09PB3-mQBUi3DnltrVt4IfEwaumDloPbVlkSTBQcMnaNTFTov6LY4whwVxdPy4o6aQsQiIiUH3IZsEBVtZhl9Q-5Xn0jGqnRFHlRY0iMKijON6SAXPvRDjk9WyW4S6aIa6X03W1ON8ZN4sYXCstZLCkcydKsR3Tsapiv6v-NUPA4bFtn6w29aEWCUW_e5GPa17qsKrQwjhZnVL8-ZdZNwU9PppQTz0EQrngcBRmDfbzPU9_Z2tXFClZj9SqARaR2rVnR4siGwc6Fvyu_47OUaUoNV1H22igD-sNmhzKmlw_Rg-4z5pDizbUAFIm3kHK5zYMBPUQXoQhnB-3DoQcBhrbaO4KhcEVx0Ug
    ##  ---                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
    ## 227: You are not authorized to perform this operation. Encoded authorization failure message: sFso9_AhbnX87-4WNPO-4L46kGsRRl6ejlV5PfeDA8K0QQXYMPEfXWeDJLITI9xAPvtmEKd8dDyGk2iEhAruo7GoTbTkUBRXkeqVtU9wvVE_HQaXMFdGX1FOdw6ff9KnCZrLNJOHCmnV_tQnt4V4HhewieshNc3URQ6-jvNMYjTztb9cp8vrE9tjNIkz5j47XN4FR3F-26qPHNgOW582_nYOSv-R1sEQUe6QAcUMaTuMPUVw8pU2xePiAPjs8s9G3ycxyZI3pMXDBXTCP4v1Tu6VR-q0iF9DUG8PBk5vB9_VSH7RUiw9HVfoulhSOx6KIms71VxzmURHKFx2imUUFIgTduBXFfDZV8GGr1diVW8_CDqWqXgIbh-jzDeafYtO66KYSGoGZ-zQlHbHuNo0qFW0_m0geqhdr5LUwgPsDnp_CO_HwFX1ZoWawKYq748peb22SfdWsf-CFRaFOvaZoQjOrCX34aJoO4gKaz0UA-pht4-a7rfxYUJcFzbnXrOOZkOzek0vl3_vMh4hdWRa21rv6j5IFw63HAXA-B6VII93oLO-7pUNBoRnQgnnzKeRL2i_ZpNg5RGfe3DipPVrzKCmjaQnVpPKQCkZs7JdpX8GPvDwcEEVZ1MOdHrX62HGR85SbkB05BorOpcKV8d8kHf7iP7P2tEr80IQsqFjglY
    ## 228: You are not authorized to perform this operation. Encoded authorization failure message: xvZitPBwgPLNwD7syX4l0-Mv3UqLCQleg116nNGCQmXs7g6PcZh3_uGypCE2FiryY-tH1dMTQd31kpWiW3VgJm4XQT_Mhp7hbbsRrDSqp3LnbKxFZy8INHqZ_20Wa_CvsB4I5Jlit1fSvynfwTdXD158hUpkDd7765L2bYO0j5U81D6qRfn7FG5yuLM3sB9Gk9SCQpCohYWT2piA0TUCqGXQ1TjqG5sCsxOnb5ekBUDk5pXB2cLpvw-04gK7Ovbaf1PY8c0zNY9MdyaK9u68gsljBlMyIJMpdF1TqfcIm6e-gQGnbBHnJvFUW1k7D98YhJc2OBO12oRQ7mcsUwm_zqlhFOsujif0-AYthNECskAIx9Pf-Yr1uCgi1wcIZn88zaT-DP-Osrlm5E3uyZPyw9jq-fZ3SgjWGzzKN0A5B83WbpFj_4F71Y6z-fBuDomyYMAgCcU9gChN2-OX1PGJcY7rNWx7Hs39yxNL5s8tuYsttOA7cSsmoPoCnfuH7Ccvy2KH4BaB8Ea0HqTaCr1Negz7PxqpxJnnJd_LJCc5REElC4U2QRD9YAFCtMaCN2BHDd3lswb0i4U2Lp32ypEzpuY8rVXrROrSSTXg3tXzjvLAd8ZU5JueR346hHJ8y3KKekABK7MiD6BbvDvyttHFM1r0W2fs3Kf5xEqP-716LyI
    ## 229:  You are not authorized to perform this operation. Encoded authorization failure message: WkaNGddTeVqgAOdofQBkATAnLtD1czbdXR-MExrUIAezlLVXv8J1Hf_Zi5HO4HmHL77UMeMDgw9-7MoymK-2VzdGW8EB_X8iMhLWYw-6KqDi_n2iumaEvNBA2a9fbUJdoNhUPe88fzU3zhHNJlggYcTMNZOrg1tnkwQAM5aEzoewlRCa8mEcy36HUUed9UxBgQclsibd0V5uNr1garIGoUhQ-yJ_xSXVI51rH7jLpAiUDQlk82dMuIf6cQVwFjpapVqeWS23PF9WnL6eA6lm7W-4FfcPh2sEPDD61V4O8D8a9OMtVkBoYk1ahh7v1Eb-KuMA-k5buyX-unFtkt49qkZOe4bxfEcdxlj_wBleAaay3vgvyYFIptOw02slofRiPufe1wQZGwLPV-KIUnjdUiJ9PPL7-lwAGQL9I1nTKtAQa8wS6K6gV8anOEbkRS3CZJsOxhc8ZZ6Ukr3PLTkSJs9lbrDp76XKblebgi_vNZHpntDKIhtRQs5JOmE3ZONaC-1OHX0e5C5jz_5UxYBx0qqZ3AOc6sPOE45TIjpMLYkERlRovuIx8UHxYczHUUiZD1DdC9h0Is3qv3OhZRfiPVc3XIOykCQ5PNGFz-ej5qkWTancwRX_eKjlmjHnpyevR6CozU7ct4fhVDn1vku7UzwtAOBAhon1OJlUouvtOg
    ## 230: You are not authorized to perform this operation. Encoded authorization failure message: 3lDHOCCsUvr52KUDdk74MpoxaHTr5rOX6Cwb3k7ZbWtA0RsMyARKNK8JAP-7FIx6nzGcDeeMG8Eei5YUbbdKkLdNAvEClAon0qkvOQbr4ofJnjBFsxlQegvg-mo0kQ2YCneyVw-kj4A4E4dUby_zUPyVLyb1_PWTg-OmyMBE3X6V2scEEOrjS0S_7Xk7-2LUbLFH4lgeRn1qAED_MPiSRCmBcKo_SRJ90BC4oB_C6uKTchWl2ZhCitFucYwZBlTTtK7G9rBXj7jyEvIz0QSNwYXW4b4eaTv4nVbI2vN80odXID0HhRSbn-RujsE_B2P_zy4xvWkGZdNiG--PgT54vi0ijIfDkbdfmbsDetJJL4J1_pTkWU7vMV_9XKetFiniorBgzf7tDx8CbCPQWs-0ro0V-rSqIvP7nA341aSkzDRdpP45rno2EzSfwhg7IzsnHbfZ6mzeM50SdHbsl4vnGZEZxsJwgA8OQU-4a4vI4k3sa7bS_SSLva3xRXhIiO4yo7VMvJcoI7SsmKYlj3BI8pWh5UcE2ZzA1DYGmEisYxhb0wTQ_TR17h3WC4MaZRFpZ47Uz1bDA4tidtDvDiaLTwNW1cJGwugThWQ-9QEF-zIzNq6Cz7eNehAqPAZuAQXyg3-8ZijyIp2FSeCbxZ7afEsRmGxL26AmPwPF7egmxaY
    ## 231:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    You are not authorized to perform this operation.
    ##      recipientAccountId         region                            requestID
    ##   1:           6.23e+11      eu-west-1 efb4aa67-721a-4498-9de3-dddcbd1cad76
    ##   2:           6.23e+11      eu-west-1 da57718b-3c0d-4c4b-81ee-2ac7d5141b33
    ##   3:           6.23e+11      eu-west-1 47608c96-c373-4b50-a01b-e2fb67126b58
    ##   4:           6.23e+11      eu-west-1 4d42a81f-8b8b-4f3a-91c5-c1a1a8951800
    ##   5:           6.23e+11      eu-west-1 4a13a9d1-68eb-4880-a4ab-55e467ed32f3
    ##  ---                                                                       
    ## 227:           6.23e+11 ap-northeast-2 88b73548-211e-4491-b8e0-19513a172630
    ## 228:           6.23e+11 ap-northeast-2 a2648809-b914-4465-aaa1-de79b08d8067
    ## 229:           6.23e+11 ap-northeast-2 1d39afea-80fe-4a3c-b578-fa597ec525d6
    ## 230:           6.23e+11 ap-northeast-2 7e66d8dd-f28e-49ba-9624-ceffb76ad8bb
    ## 231:           6.23e+11      us-east-1 f94dfb04-2d7b-40a8-b3cc-3664b9463db8
    ##      requestParameters
    ##   1:                  
    ##   2:                  
    ##   3:                  
    ##   4:                  
    ##   5:                  
    ##  ---                  
    ## 227:                  
    ## 228:                  
    ## 229:                  
    ## 230:                  
    ## 231:                  
    ##      requestParameters.AccessControlPolicy.AccessControlList.Grant{}.Grantee.DisplayName
    ##   1:                                                                                    
    ##   2:                                                                                    
    ##   3:                                                                                    
    ##   4:                                                                                    
    ##   5:                                                                                    
    ##  ---                                                                                    
    ## 227:                                                                                    
    ## 228:                                                                                    
    ## 229:                                                                                    
    ## 230:                                                                                    
    ## 231:                                                                                    
    ##      requestParameters.AccessControlPolicy.AccessControlList.Grant{}.Grantee.ID
    ##   1:                                                                           
    ##   2:                                                                           
    ##   3:                                                                           
    ##   4:                                                                           
    ##   5:                                                                           
    ##  ---                                                                           
    ## 227:                                                                           
    ## 228:                                                                           
    ## 229:                                                                           
    ## 230:                                                                           
    ## 231:                                                                           
    ##      requestParameters.AccessControlPolicy.AccessControlList.Grant{}.Grantee.URI
    ##   1:                                                                            
    ##   2:                                                                            
    ##   3:                                                                            
    ##   4:                                                                            
    ##   5:                                                                            
    ##  ---                                                                            
    ## 227:                                                                            
    ## 228:                                                                            
    ## 229:                                                                            
    ## 230:                                                                            
    ## 231:                                                                            
    ##      requestParameters.AccessControlPolicy.AccessControlList.Grant{}.Grantee.xmlns:xsi
    ##   1:                                                                                  
    ##   2:                                                                                  
    ##   3:                                                                                  
    ##   4:                                                                                  
    ##   5:                                                                                  
    ##  ---                                                                                  
    ## 227:                                                                                  
    ## 228:                                                                                  
    ## 229:                                                                                  
    ## 230:                                                                                  
    ## 231:                                                                                  
    ##      requestParameters.AccessControlPolicy.AccessControlList.Grant{}.Grantee.xsi:type
    ##   1:                                                                                 
    ##   2:                                                                                 
    ##   3:                                                                                 
    ##   4:                                                                                 
    ##   5:                                                                                 
    ##  ---                                                                                 
    ## 227:                                                                                 
    ## 228:                                                                                 
    ## 229:                                                                                 
    ## 230:                                                                                 
    ## 231:                                                                                 
    ##      requestParameters.AccessControlPolicy.AccessControlList.Grant{}.Permission
    ##   1:                                                                           
    ##   2:                                                                           
    ##   3:                                                                           
    ##   4:                                                                           
    ##   5:                                                                           
    ##  ---                                                                           
    ## 227:                                                                           
    ## 228:                                                                           
    ## 229:                                                                           
    ## 230:                                                                           
    ## 231:                                                                           
    ##      requestParameters.AccessControlPolicy.Owner.DisplayName
    ##   1:                                                        
    ##   2:                                                        
    ##   3:                                                        
    ##   4:                                                        
    ##   5:                                                        
    ##  ---                                                        
    ## 227:                                                        
    ## 228:                                                        
    ## 229:                                                        
    ## 230:                                                        
    ## 231:                                                        
    ##      requestParameters.AccessControlPolicy.Owner.ID
    ##   1:                                               
    ##   2:                                               
    ##   3:                                               
    ##   4:                                               
    ##   5:                                               
    ##  ---                                               
    ## 227:                                               
    ## 228:                                               
    ## 229:                                               
    ## 230:                                               
    ## 231:                                               
    ##      requestParameters.AccessControlPolicy.xmlns
    ##   1:                                            
    ##   2:                                            
    ##   3:                                            
    ##   4:                                            
    ##   5:                                            
    ##  ---                                            
    ## 227:                                            
    ## 228:                                            
    ## 229:                                            
    ## 230:                                            
    ## 231:                                            
    ##      requestParameters.DescribeHostsRequest.Filter.Name
    ##   1:                                                   
    ##   2:                                                   
    ##   3:                                                   
    ##   4:                                                   
    ##   5:                                                   
    ##  ---                                                   
    ## 227:                                                   
    ## 228:                                                   
    ## 229:                                                   
    ## 230:                                                   
    ## 231:                                                   
    ##      requestParameters.DescribeHostsRequest.Filter.Value.content
    ##   1:                                                            
    ##   2:                                                            
    ##   3:                                                            
    ##   4:                                                            
    ##   5:                                                            
    ##  ---                                                            
    ## 227:                                                            
    ## 228:                                                            
    ## 229:                                                            
    ## 230:                                                            
    ## 231:                                                            
    ##      requestParameters.DescribeHostsRequest.Filter.Value.tag
    ##   1:                                                      NA
    ##   2:                                                      NA
    ##   3:                                                      NA
    ##   4:                                                      NA
    ##   5:                                                      NA
    ##  ---                                                        
    ## 227:                                                      NA
    ## 228:                                                      NA
    ## 229:                                                      NA
    ## 230:                                                      NA
    ## 231:                                                      NA
    ##      requestParameters.DescribeHostsRequest.Filter.tag
    ##   1:                                                NA
    ##   2:                                                NA
    ##   3:                                                NA
    ##   4:                                                NA
    ##   5:                                                NA
    ##  ---                                                  
    ## 227:                                                NA
    ## 228:                                                NA
    ## 229:                                                NA
    ## 230:                                                NA
    ## 231:                                                NA
    ##      requestParameters.DescribeInstanceCreditSpecificationsRequest.InstanceId.content
    ##   1:                                                                                 
    ##   2:                                                                                 
    ##   3:                                                                                 
    ##   4:                                                                                 
    ##   5:                                                                                 
    ##  ---                                                                                 
    ## 227:                                                                                 
    ## 228:                                                                                 
    ## 229:                                                                                 
    ## 230:                                                                                 
    ## 231:                                                                                 
    ##      requestParameters.DescribeInstanceCreditSpecificationsRequest.InstanceId.tag
    ##   1:                                                                           NA
    ##   2:                                                                           NA
    ##   3:                                                                           NA
    ##   4:                                                                           NA
    ##   5:                                                                           NA
    ##  ---                                                                             
    ## 227:                                                                           NA
    ## 228:                                                                           NA
    ## 229:                                                                           NA
    ## 230:                                                                           NA
    ## 231:                                                                           NA
    ##      requestParameters.DescribeLaunchTemplateVersionsRequest.LaunchTemplateName
    ##   1:                                                                           
    ##   2:                                                                           
    ##   3:                                                                           
    ##   4:                                                                           
    ##   5:                                                                           
    ##  ---                                                                           
    ## 227:                                                                           
    ## 228:                                                                           
    ## 229:                                                                           
    ## 230:                                                                           
    ## 231:                                                                           
    ##      requestParameters.DescribeLaunchTemplateVersionsRequest.MaxResults
    ##   1:                                                                 NA
    ##   2:                                                                 NA
    ##   3:                                                                 NA
    ##   4:                                                                 NA
    ##   5:                                                                 NA
    ##  ---                                                                   
    ## 227:                                                                 NA
    ## 228:                                                                 NA
    ## 229:                                                                 NA
    ## 230:                                                                 NA
    ## 231:                                                                 NA
    ##      requestParameters.DescribeLaunchTemplatesRequest.MaxResults
    ##   1:                                                          NA
    ##   2:                                                          NA
    ##   3:                                                          NA
    ##   4:                                                          NA
    ##   5:                                                          NA
    ##  ---                                                            
    ## 227:                                                          NA
    ## 228:                                                          NA
    ## 229:                                                          NA
    ## 230:                                                          NA
    ## 231:                                                          NA
    ##      requestParameters.DescribeStaleSecurityGroupsRequest.MaxResults
    ##   1:                                                              NA
    ##   2:                                                              NA
    ##   3:                                                              NA
    ##   4:                                                              NA
    ##   5:                                                              NA
    ##  ---                                                                
    ## 227:                                                              NA
    ## 228:                                                              NA
    ## 229:                                                              NA
    ## 230:                                                              NA
    ## 231:                                                              NA
    ##      requestParameters.DescribeStaleSecurityGroupsRequest.VpcId
    ##   1:                                                           
    ##   2:                                                           
    ##   3:                                                           
    ##   4:                                                           
    ##   5:                                                           
    ##  ---                                                           
    ## 227:                                                           
    ## 228:                                                           
    ## 229:                                                           
    ## 230:                                                           
    ## 231:                                                           
    ##      requestParameters.DescribeVolumesModificationsRequest.MaxResults
    ##   1:                                                               NA
    ##   2:                                                               NA
    ##   3:                                                               NA
    ##   4:                                                               NA
    ##   5:                                                               NA
    ##  ---                                                                 
    ## 227:                                                               NA
    ## 228:                                                               NA
    ## 229:                                                               NA
    ## 230:                                                               NA
    ## 231:                                                               NA
    ##      requestParameters.GetConsoleScreenshotRequest.InstanceId
    ##   1:                                                         
    ##   2:                                                         
    ##   3:                                                         
    ##   4:                                                         
    ##   5:                                                         
    ##  ---                                                         
    ## 227:                                                         
    ## 228:                                                         
    ## 229:                                                         
    ## 230:                                                         
    ## 231:                                                         
    ##      requestParameters.GetConsoleScreenshotRequest.WakeUp
    ##   1:                                                   NA
    ##   2:                                                   NA
    ##   3:                                                   NA
    ##   4:                                                   NA
    ##   5:                                                   NA
    ##  ---                                                     
    ## 227:                                                   NA
    ## 228:                                                   NA
    ## 229:                                                   NA
    ## 230:                                                   NA
    ## 231:                                                   NA
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.GroupId
    ##   1:                                                                            
    ##   2:                                                                            
    ##   3:                                                                            
    ##   4:                                                                            
    ##   5:                                                                            
    ##  ---                                                                            
    ## 227:                                                                            
    ## 228:                                                                            
    ## 229:                                                                            
    ## 230:                                                                            
    ## 231:                                                                            
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.FromPort
    ##   1:                                                                                             
    ##   2:                                                                                             
    ##   3:                                                                                             
    ##   4:                                                                                             
    ##   5:                                                                                             
    ##  ---                                                                                             
    ## 227:                                                                                             
    ## 228:                                                                                             
    ## 229:                                                                                             
    ## 230:                                                                                             
    ## 231:                                                                                             
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.IpProtocol
    ##   1:                                                                                               
    ##   2:                                                                                               
    ##   3:                                                                                               
    ##   4:                                                                                               
    ##   5:                                                                                               
    ##  ---                                                                                               
    ## 227:                                                                                               
    ## 228:                                                                                               
    ## 229:                                                                                               
    ## 230:                                                                                               
    ## 231:                                                                                               
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.IpRanges.CidrIp
    ##   1:                                                                                                    
    ##   2:                                                                                                    
    ##   3:                                                                                                    
    ##   4:                                                                                                    
    ##   5:                                                                                                    
    ##  ---                                                                                                    
    ## 227:                                                                                                    
    ## 228:                                                                                                    
    ## 229:                                                                                                    
    ## 230:                                                                                                    
    ## 231:                                                                                                    
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.IpRanges.Description
    ##   1:                                                                                                         
    ##   2:                                                                                                         
    ##   3:                                                                                                         
    ##   4:                                                                                                         
    ##   5:                                                                                                         
    ##  ---                                                                                                         
    ## 227:                                                                                                         
    ## 228:                                                                                                         
    ## 229:                                                                                                         
    ## 230:                                                                                                         
    ## 231:                                                                                                         
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.IpRanges.tag
    ##   1:                                                                                               NA
    ##   2:                                                                                               NA
    ##   3:                                                                                               NA
    ##   4:                                                                                               NA
    ##   5:                                                                                               NA
    ##  ---                                                                                                 
    ## 227:                                                                                               NA
    ## 228:                                                                                               NA
    ## 229:                                                                                               NA
    ## 230:                                                                                               NA
    ## 231:                                                                                               NA
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.Ipv6Ranges.CidrIpv6
    ##   1:                                                                                                        
    ##   2:                                                                                                        
    ##   3:                                                                                                        
    ##   4:                                                                                                        
    ##   5:                                                                                                        
    ##  ---                                                                                                        
    ## 227:                                                                                                        
    ## 228:                                                                                                        
    ## 229:                                                                                                        
    ## 230:                                                                                                        
    ## 231:                                                                                                        
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.Ipv6Ranges.Description
    ##   1:                                                                                                           
    ##   2:                                                                                                           
    ##   3:                                                                                                           
    ##   4:                                                                                                           
    ##   5:                                                                                                           
    ##  ---                                                                                                           
    ## 227:                                                                                                           
    ## 228:                                                                                                           
    ## 229:                                                                                                           
    ## 230:                                                                                                           
    ## 231:                                                                                                           
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.Ipv6Ranges.tag
    ##   1:                                                                                                 NA
    ##   2:                                                                                                 NA
    ##   3:                                                                                                 NA
    ##   4:                                                                                                 NA
    ##   5:                                                                                                 NA
    ##  ---                                                                                                   
    ## 227:                                                                                                 NA
    ## 228:                                                                                                 NA
    ## 229:                                                                                                 NA
    ## 230:                                                                                                 NA
    ## 231:                                                                                                 NA
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.ToPort
    ##   1:                                                                                           
    ##   2:                                                                                           
    ##   3:                                                                                           
    ##   4:                                                                                           
    ##   5:                                                                                           
    ##  ---                                                                                           
    ## 227:                                                                                           
    ## 228:                                                                                           
    ## 229:                                                                                           
    ## 230:                                                                                           
    ## 231:                                                                                           
    ##      requestParameters.UpdateSecurityGroupRuleDescriptionsIngressRequest.IpPermissions{}.tag
    ##   1:                                                                                        
    ##   2:                                                                                        
    ##   3:                                                                                        
    ##   4:                                                                                        
    ##   5:                                                                                        
    ##  ---                                                                                        
    ## 227:                                                                                        
    ## 228:                                                                                        
    ## 229:                                                                                        
    ## 230:                                                                                        
    ## 231:                                                                                        
    ##      requestParameters.accessKeyId
    ##   1:                              
    ##   2:                              
    ##   3:                              
    ##   4:                              
    ##   5:                              
    ##  ---                              
    ## 227:                              
    ## 228:                              
    ## 229:                              
    ## 230:                              
    ## 231:                              
    ##      requestParameters.accountAttributeNameSet.items{}.attributeName
    ##   1:                                                                
    ##   2:                                                                
    ##   3:                                                                
    ##   4:                                                                
    ##   5:                                                                
    ##  ---                                                                
    ## 227:                                                                
    ## 228:                                                                
    ## 229:                                                                
    ## 230:                                                                
    ## 231:                                                                
    ##      requestParameters.acl{} requestParameters.attribute
    ##   1:                      NA                            
    ##   2:                      NA                            
    ##   3:                      NA                            
    ##   4:                      NA                            
    ##   5:                      NA                            
    ##  ---                                                    
    ## 227:                      NA                            
    ## 228:                      NA                            
    ## 229:                      NA                            
    ## 230:                      NA                            
    ## 231:                      NA                            
    ##      requestParameters.autoScalingGroupName
    ##   1:                                       
    ##   2:                                       
    ##   3:                                       
    ##   4:                                       
    ##   5:                                       
    ##  ---                                       
    ## 227:                                       
    ## 228:                                       
    ## 229:                                       
    ## 230:                                       
    ## 231:                                       
    ##      requestParameters.autoScalingGroupNames{}
    ##   1:                                          
    ##   2:                                          
    ##   3:                                          
    ##   4:                                          
    ##   5:                                          
    ##  ---                                          
    ## 227:                                          
    ## 228:                                          
    ## 229:                                          
    ## 230:                                          
    ## 231:                                          
    ##      requestParameters.blockDeviceMapping.items{}.deviceName
    ##   1:                                                        
    ##   2:                                                        
    ##   3:                                                        
    ##   4:                                                        
    ##   5:                                                        
    ##  ---                                                        
    ## 227:                                                        
    ## 228:                                                        
    ## 229:                                                        
    ## 230:                                                        
    ## 231:                                                        
    ##      requestParameters.blockDeviceMapping.items{}.ebs.deleteOnTermination
    ##   1:                                                                   NA
    ##   2:                                                                   NA
    ##   3:                                                                   NA
    ##   4:                                                                   NA
    ##   5:                                                                   NA
    ##  ---                                                                     
    ## 227:                                                                   NA
    ## 228:                                                                   NA
    ## 229:                                                                   NA
    ## 230:                                                                   NA
    ## 231:                                                                   NA
    ##      requestParameters.blockDeviceMapping.items{}.ebs.volumeType
    ##   1:                                                            
    ##   2:                                                            
    ##   3:                                                            
    ##   4:                                                            
    ##   5:                                                            
    ##  ---                                                            
    ## 227:                                                            
    ## 228:                                                            
    ## 229:                                                            
    ## 230:                                                            
    ## 231:                                                            
    ##      requestParameters.bucketName requestParameters.configRuleName
    ##   1:                                                              
    ##   2:                                                              
    ##   3:                                                              
    ##   4:                                                              
    ##   5:                                                              
    ##  ---                                                              
    ## 227:                                                              
    ## 228:                                                              
    ## 229:                                                              
    ## 230:                                                              
    ## 231:                                                              
    ##      requestParameters.configRuleNames{} requestParameters.cors{}
    ##   1:                                                           NA
    ##   2:                                                           NA
    ##   3:                                                           NA
    ##   4:                                                           NA
    ##   5:                                                           NA
    ##  ---                                                             
    ## 227:                                                           NA
    ## 228:                                                           NA
    ## 229:                                                           NA
    ## 230:                                                           NA
    ## 231:                                                           NA
    ##      requestParameters.disableApiTermination requestParameters.durationSeconds
    ##   1:                                    TRUE                                NA
    ##   2:                                      NA                                NA
    ##   3:                                    TRUE                                NA
    ##   4:                                    TRUE                                NA
    ##   5:                                    TRUE                                NA
    ##  ---                                                                          
    ## 227:                                    TRUE                                NA
    ## 228:                                    TRUE                                NA
    ## 229:                                    TRUE                                NA
    ## 230:                                    TRUE                                NA
    ## 231:                                      NA                                NA
    ##      requestParameters.encryptionContext.aws:lambda:FunctionArn
    ##   1:                                                           
    ##   2:                                                           
    ##   3:                                                           
    ##   4:                                                           
    ##   5:                                                           
    ##  ---                                                           
    ## 227:                                                           
    ## 228:                                                           
    ## 229:                                                           
    ## 230:                                                           
    ## 231:                                                           
    ##      requestParameters.encryption{}
    ##   1:                             NA
    ##   2:                             NA
    ##   3:                             NA
    ##   4:                             NA
    ##   5:                             NA
    ##  ---                               
    ## 227:                             NA
    ## 228:                             NA
    ## 229:                             NA
    ## 230:                             NA
    ## 231:                             NA
    ##      requestParameters.filter.completionTimeRange.beginDate
    ##   1:                                                       
    ##   2:                                                       
    ##   3:                                                       
    ##   4:                                                       
    ##   5:                                                       
    ##  ---                                                       
    ## 227:                                                       
    ## 228:                                                       
    ## 229:                                                       
    ## 230:                                                       
    ## 231:                                                       
    ##      requestParameters.filter.completionTimeRange.endDate
    ##   1:                                                     
    ##   2:                                                     
    ##   3:                                                     
    ##   4:                                                     
    ##   5:                                                     
    ##  ---                                                     
    ## 227:                                                     
    ## 228:                                                     
    ## 229:                                                     
    ## 230:                                                     
    ## 231:                                                     
    ##      requestParameters.filter.creationTimeRange.beginDate
    ##   1:                                                     
    ##   2:                                                     
    ##   3:                                                     
    ##   4:                                                     
    ##   5:                                                     
    ##  ---                                                     
    ## 227:                                                     
    ## 228:                                                     
    ## 229:                                                     
    ## 230:                                                     
    ## 231:                                                     
    ##      requestParameters.filter.creationTimeRange.endDate
    ##   1:                                                   
    ##   2:                                                   
    ##   3:                                                   
    ##   4:                                                   
    ##   5:                                                   
    ##  ---                                                   
    ## 227:                                                   
    ## 228:                                                   
    ## 229:                                                   
    ## 230:                                                   
    ## 231:                                                   
    ##      requestParameters.filterSet.items{}.name
    ##   1:                                         
    ##   2:                                         
    ##   3:                                         
    ##   4:                                         
    ##   5:                                         
    ##  ---                                         
    ## 227:                                         
    ## 228:                                         
    ## 229:                                         
    ## 230:                                         
    ## 231:                                         
    ##      requestParameters.filterSet.items{}.valueSet.items{}.value
    ##   1:                                                           
    ##   2:                                                           
    ##   3:                                                           
    ##   4:                                                           
    ##   5:                                                           
    ##  ---                                                           
    ## 227:                                                           
    ## 228:                                                           
    ## 229:                                                           
    ## 230:                                                           
    ## 231:                                                           
    ##      requestParameters.groupId requestParameters.imagesSet.items{}.imageId
    ##   1:                                                                      
    ##   2:                                                                      
    ##   3:                                                                      
    ##   4:                                                                      
    ##   5:                                                                      
    ##  ---                                                                      
    ## 227:                                                                      
    ## 228:                                                                      
    ## 229:                                                                      
    ## 230:                                                                      
    ## 231:                                                                      
    ##      requestParameters.includeAllInstances requestParameters.instanceId
    ##   1:                                    NA                             
    ##   2:                                    NA                             
    ##   3:                                    NA                             
    ##   4:                                    NA                             
    ##   5:                                    NA                             
    ##  ---                                                                   
    ## 227:                                    NA                             
    ## 228:                                    NA                             
    ## 229:                                    NA                             
    ## 230:                                    NA                             
    ## 231:                                    NA                             
    ##      requestParameters.instanceType
    ##   1:                     c3.4xlarge
    ##   2:                               
    ##   3:                     c3.8xlarge
    ##   4:                     r3.8xlarge
    ##   5:                     c4.4xlarge
    ##  ---                               
    ## 227:                     c4.2xlarge
    ## 228:                     m4.2xlarge
    ## 229:                     t2.2xlarge
    ## 230:                     c4.8xlarge
    ## 231:                               
    ##      requestParameters.instancesSet.items{}.imageId
    ##   1:                                   ami-4d46d534
    ##   2:                                               
    ##   3:                                   ami-4d46d534
    ##   4:                                   ami-4d46d534
    ##   5:                                   ami-4d46d534
    ##  ---                                               
    ## 227:                                   ami-67973709
    ## 228:                                   ami-67973709
    ## 229:                                   ami-67973709
    ## 230:                                   ami-67973709
    ## 231:                                               
    ##      requestParameters.instancesSet.items{}.instanceId
    ##   1:                                                  
    ##   2:                                                  
    ##   3:                                                  
    ##   4:                                                  
    ##   5:                                                  
    ##  ---                                                  
    ## 227:                                                  
    ## 228:                                                  
    ## 229:                                                  
    ## 230:                                                  
    ## 231:                                                  
    ##      requestParameters.instancesSet.items{}.maxCount
    ##   1:                                              10
    ##   2:                                              NA
    ##   3:                                              10
    ##   4:                                              10
    ##   5:                                              10
    ##  ---                                                
    ## 227:                                              10
    ## 228:                                              10
    ## 229:                                              10
    ## 230:                                              10
    ## 231:                                              NA
    ##      requestParameters.instancesSet.items{}.minCount
    ##   1:                                               1
    ##   2:                                              NA
    ##   3:                                               1
    ##   4:                                               1
    ##   5:                                               1
    ##  ---                                                
    ## 227:                                               1
    ## 228:                                               1
    ## 229:                                               1
    ## 230:                                               1
    ## 231:                                              NA
    ##      requestParameters.ipPermissions.items{}.fromPort
    ##   1:                                                 
    ##   2:                                                 
    ##   3:                                                 
    ##   4:                                                 
    ##   5:                                                 
    ##  ---                                                 
    ## 227:                                                 
    ## 228:                                                 
    ## 229:                                                 
    ## 230:                                                 
    ## 231:                                                 
    ##      requestParameters.ipPermissions.items{}.ipProtocol
    ##   1:                                                   
    ##   2:                                                   
    ##   3:                                                   
    ##   4:                                                   
    ##   5:                                                   
    ##  ---                                                   
    ## 227:                                                   
    ## 228:                                                   
    ## 229:                                                   
    ## 230:                                                   
    ## 231:                                                   
    ##      requestParameters.ipPermissions.items{}.ipRanges.items{}.cidrIp
    ##   1:                                                                
    ##   2:                                                                
    ##   3:                                                                
    ##   4:                                                                
    ##   5:                                                                
    ##  ---                                                                
    ## 227:                                                                
    ## 228:                                                                
    ## 229:                                                                
    ## 230:                                                                
    ## 231:                                                                
    ##      requestParameters.ipPermissions.items{}.ipRanges.items{}.description
    ##   1:                                                                     
    ##   2:                                                                     
    ##   3:                                                                     
    ##   4:                                                                     
    ##   5:                                                                     
    ##  ---                                                                     
    ## 227:                                                                     
    ## 228:                                                                     
    ## 229:                                                                     
    ## 230:                                                                     
    ## 231:                                                                     
    ##      requestParameters.ipPermissions.items{}.ipv6Ranges.items{}.cidrIpv6
    ##   1:                                                                    
    ##   2:                                                                    
    ##   3:                                                                    
    ##   4:                                                                    
    ##   5:                                                                    
    ##  ---                                                                    
    ## 227:                                                                    
    ## 228:                                                                    
    ## 229:                                                                    
    ## 230:                                                                    
    ## 231:                                                                    
    ##      requestParameters.ipPermissions.items{}.ipv6Ranges.items{}.description
    ##   1:                                                                       
    ##   2:                                                                       
    ##   3:                                                                       
    ##   4:                                                                       
    ##   5:                                                                       
    ##  ---                                                                       
    ## 227:                                                                       
    ## 228:                                                                       
    ## 229:                                                                       
    ## 230:                                                                       
    ## 231:                                                                       
    ##      requestParameters.ipPermissions.items{}.toPort
    ##   1:                                               
    ##   2:                                               
    ##   3:                                               
    ##   4:                                               
    ##   5:                                               
    ##  ---                                               
    ## 227:                                               
    ## 228:                                               
    ## 229:                                               
    ## 230:                                               
    ## 231:                                               
    ##      requestParameters.lifecycle{} requestParameters.limit
    ##   1:                            NA                      NA
    ##   2:                            NA                      NA
    ##   3:                            NA                      NA
    ##   4:                            NA                      NA
    ##   5:                            NA                      NA
    ##  ---                                                      
    ## 227:                            NA                      NA
    ## 228:                            NA                      NA
    ## 229:                            NA                      NA
    ## 230:                            NA                      NA
    ## 231:                            NA                      NA
    ##      requestParameters.loadBalancerArn requestParameters.location{}
    ##   1:                                                             NA
    ##   2:                                                             NA
    ##   3:                                                             NA
    ##   4:                                                             NA
    ##   5:                                                             NA
    ##  ---                                                               
    ## 227:                                                             NA
    ## 228:                                                             NA
    ## 229:                                                             NA
    ## 230:                                                             NA
    ## 231:                                                             NA
    ##      requestParameters.logging{} requestParameters.maxItems
    ##   1:                          NA                         NA
    ##   2:                          NA                         NA
    ##   3:                          NA                         NA
    ##   4:                          NA                         NA
    ##   5:                          NA                         NA
    ##  ---                                                       
    ## 227:                          NA                         NA
    ## 228:                          NA                         NA
    ## 229:                          NA                         NA
    ## 230:                          NA                         NA
    ## 231:                          NA                         NA
    ##      requestParameters.maxRecords requestParameters.maxResults
    ##   1:                           NA                           NA
    ##   2:                           NA                           NA
    ##   3:                           NA                           NA
    ##   4:                           NA                           NA
    ##   5:                           NA                           NA
    ##  ---                                                          
    ## 227:                           NA                           NA
    ## 228:                           NA                           NA
    ## 229:                           NA                           NA
    ## 230:                           NA                           NA
    ## 231:                           NA                           NA
    ##      requestParameters.monitoring.enabled requestParameters.nextToken
    ##   1:                                FALSE                            
    ##   2:                                   NA                            
    ##   3:                                FALSE                            
    ##   4:                                FALSE                            
    ##   5:                                FALSE                            
    ##  ---                                                                 
    ## 227:                                FALSE                            
    ## 228:                                FALSE                            
    ## 229:                                FALSE                            
    ## 230:                                FALSE                            
    ## 231:                                   NA                            
    ##      requestParameters.notification{} requestParameters.ownersSet.items{}.owner
    ##   1:                               NA                                          
    ##   2:                               NA                                          
    ##   3:                               NA                                          
    ##   4:                               NA                                          
    ##   5:                               NA                                          
    ##  ---                                                                           
    ## 227:                               NA                                          
    ## 228:                               NA                                          
    ## 229:                               NA                                          
    ## 230:                               NA                                          
    ## 231:                               NA                                          
    ##      requestParameters.pageSize requestParameters.pathPrefix
    ##   1:                         NA                             
    ##   2:                         NA                             
    ##   3:                         NA                             
    ##   4:                         NA                             
    ##   5:                         NA                             
    ##  ---                                                        
    ## 227:                         NA                             
    ## 228:                         NA                             
    ## 229:                         NA                             
    ## 230:                         NA                             
    ## 231:                         NA                             
    ##      requestParameters.policyName requestParameters.policyNames{}
    ##   1:                                                             
    ##   2:                                                             
    ##   3:                                                             
    ##   4:                                                             
    ##   5:                                                             
    ##  ---                                                             
    ## 227:                                                             
    ## 228:                                                             
    ## 229:                                                             
    ## 230:                                                             
    ## 231:                                                             
    ##      requestParameters.policyType requestParameters.policy{}
    ##   1:                                                      NA
    ##   2:                                                      NA
    ##   3:                                                      NA
    ##   4:                                                      NA
    ##   5:                                                      NA
    ##  ---                                                        
    ## 227:                                                      NA
    ## 228:                                                      NA
    ## 229:                                                      NA
    ## 230:                                                      NA
    ## 231:                                                      NA
    ##      requestParameters.replication{} requestParameters.requestPayment{}
    ##   1:                              NA                                 NA
    ##   2:                              NA                                 NA
    ##   3:                              NA                                 NA
    ##   4:                              NA                                 NA
    ##   5:                              NA                                 NA
    ##  ---                                                                   
    ## 227:                              NA                                 NA
    ## 228:                              NA                                 NA
    ## 229:                              NA                                 NA
    ## 230:                              NA                                 NA
    ## 231:                              NA                                 NA
    ##      requestParameters.resourceArns{}
    ##   1:                                 
    ##   2:                                 
    ##   3:                                 
    ##   4:                                 
    ##   5:                                 
    ##  ---                                 
    ## 227:                                 
    ## 228:                                 
    ## 229:                                 
    ## 230:                                 
    ## 231:                                 
    ##      requestParameters.securityGroupIdSet.items{}.groupId
    ##   1:                                                     
    ##   2:                                                     
    ##   3:                                                     
    ##   4:                                                     
    ##   5:                                                     
    ##  ---                                                     
    ## 227:                                                     
    ## 228:                                                     
    ## 229:                                                     
    ## 230:                                                     
    ## 231:                                                     
    ##      requestParameters.serviceName
    ##   1:                              
    ##   2:                              
    ##   3:                              
    ##   4:                              
    ##   5:                              
    ##  ---                              
    ## 227:                              
    ## 228:                              
    ## 229:                              
    ## 230:                              
    ## 231:                              
    ##      requestParameters.sharedUsersSet.items{}.user requestParameters.status
    ##   1:                                                                       
    ##   2:                                                                       
    ##   3:                                                                       
    ##   4:                                                                       
    ##   5:                                                                       
    ##  ---                                                                       
    ## 227:                                                                       
    ## 228:                                                                       
    ## 229:                                                                       
    ## 230:                                                                       
    ## 231:                                                                       
    ##      requestParameters.tagSpecificationSet.items{}.resourceType
    ##   1:                                                   instance
    ##   2:                                                           
    ##   3:                                                   instance
    ##   4:                                                   instance
    ##   5:                                                   instance
    ##  ---                                                           
    ## 227:                                                   instance
    ## 228:                                                   instance
    ## 229:                                                   instance
    ## 230:                                                   instance
    ## 231:                                                           
    ##      requestParameters.tagSpecificationSet.items{}.tags{}.key
    ##   1:                                                 my_i_key
    ##   2:                                                         
    ##   3:                                                 my_i_key
    ##   4:                                                 my_i_key
    ##   5:                                                 my_i_key
    ##  ---                                                         
    ## 227:                                                 my_i_key
    ## 228:                                                 my_i_key
    ## 229:                                                 my_i_key
    ## 230:                                                 my_i_key
    ## 231:                                                         
    ##      requestParameters.tagSpecificationSet.items{}.tags{}.value
    ##   1:                                                   my_i_val
    ##   2:                                                           
    ##   3:                                                   my_i_val
    ##   4:                                                   my_i_val
    ##   5:                                                   my_i_val
    ##  ---                                                           
    ## 227:                                                   my_i_val
    ## 228:                                                   my_i_val
    ## 229:                                                   my_i_val
    ## 230:                                                   my_i_val
    ## 231:                                                           
    ##      requestParameters.tagging{} requestParameters.targetGroupArn
    ##   1:                          NA                                 
    ##   2:                          NA                                 
    ##   3:                          NA                                 
    ##   4:                          NA                                 
    ##   5:                          NA                                 
    ##  ---                                                             
    ## 227:                          NA                                 
    ## 228:                          NA                                 
    ## 229:                          NA                                 
    ## 230:                          NA                                 
    ## 231:                          NA                                 
    ##      requestParameters.targetTrackingConfiguration.disableScaleIn
    ##   1:                                                           NA
    ##   2:                                                           NA
    ##   3:                                                           NA
    ##   4:                                                           NA
    ##   5:                                                           NA
    ##  ---                                                             
    ## 227:                                                           NA
    ## 228:                                                           NA
    ## 229:                                                           NA
    ## 230:                                                           NA
    ## 231:                                                           NA
    ##      requestParameters.targetTrackingConfiguration.predefinedMetricSpecification.predefinedMetricType
    ##   1:                                                                                                 
    ##   2:                                                                                                 
    ##   3:                                                                                                 
    ##   4:                                                                                                 
    ##   5:                                                                                                 
    ##  ---                                                                                                 
    ## 227:                                                                                                 
    ## 228:                                                                                                 
    ## 229:                                                                                                 
    ## 230:                                                                                                 
    ## 231:                                                                                                 
    ##      requestParameters.targetTrackingConfiguration.targetValue
    ##   1:                                                        NA
    ##   2:                                                        NA
    ##   3:                                                        NA
    ##   4:                                                        NA
    ##   5:                                                        NA
    ##  ---                                                          
    ## 227:                                                        NA
    ## 228:                                                        NA
    ## 229:                                                        NA
    ## 230:                                                        NA
    ## 231:                                                        NA
    ##      requestParameters.userData requestParameters.userName
    ##   1:     <sensitiveDataRemoved>                           
    ##   2:                                                      
    ##   3:     <sensitiveDataRemoved>                           
    ##   4:     <sensitiveDataRemoved>                           
    ##   5:     <sensitiveDataRemoved>                           
    ##  ---                                                      
    ## 227:     <sensitiveDataRemoved>                           
    ## 228:     <sensitiveDataRemoved>                           
    ## 229:     <sensitiveDataRemoved>                           
    ## 230:     <sensitiveDataRemoved>                           
    ## 231:                                                      
    ##      requestParameters.versioning{}
    ##   1:                             NA
    ##   2:                             NA
    ##   3:                             NA
    ##   4:                             NA
    ##   5:                             NA
    ##  ---                               
    ## 227:                             NA
    ## 228:                             NA
    ## 229:                             NA
    ## 230:                             NA
    ## 231:                             NA
    ##      requestParameters.volumeSet.items{}.volumeId requestParameters.website{}
    ##   1:                                                                       NA
    ##   2:                                                                       NA
    ##   3:                                                                       NA
    ##   4:                                                                       NA
    ##   5:                                                                       NA
    ##  ---                                                                         
    ## 227:                                                                       NA
    ## 228:                                                                       NA
    ## 229:                                                                       NA
    ## 230:                                                                       NA
    ## 231:                                                                       NA
    ##      resources{}.ARN resources{}.accountId resources{}.type responseElements
    ##   1:                                    NA                              null
    ##   2:                                    NA                              null
    ##   3:                                    NA                              null
    ##   4:                                    NA                              null
    ##   5:                                    NA                              null
    ##  ---                                                                        
    ## 227:                                    NA                              null
    ## 228:                                    NA                              null
    ## 229:                                    NA                              null
    ## 230:                                    NA                              null
    ## 231:                                    NA                              null
    ##      responseElements.ConsoleLogin
    ##   1:                              
    ##   2:                              
    ##   3:                              
    ##   4:                              
    ##   5:                              
    ##  ---                              
    ## 227:                              
    ## 228:                              
    ## 229:                              
    ## 230:                              
    ## 231:                              
    ##      responseElements.UpdateSecurityGroupRuleDescriptionsIngressResponse.requestId
    ##   1:                                                                              
    ##   2:                                                                              
    ##   3:                                                                              
    ##   4:                                                                              
    ##   5:                                                                              
    ##  ---                                                                              
    ## 227:                                                                              
    ## 228:                                                                              
    ## 229:                                                                              
    ## 230:                                                                              
    ## 231:                                                                              
    ##      responseElements.UpdateSecurityGroupRuleDescriptionsIngressResponse.return
    ##   1:                                                                         NA
    ##   2:                                                                         NA
    ##   3:                                                                         NA
    ##   4:                                                                         NA
    ##   5:                                                                         NA
    ##  ---                                                                           
    ## 227:                                                                         NA
    ## 228:                                                                         NA
    ## 229:                                                                         NA
    ## 230:                                                                         NA
    ## 231:                                                                         NA
    ##      responseElements.UpdateSecurityGroupRuleDescriptionsIngressResponse.xmlns
    ##   1:                                                                          
    ##   2:                                                                          
    ##   3:                                                                          
    ##   4:                                                                          
    ##   5:                                                                          
    ##  ---                                                                          
    ## 227:                                                                          
    ## 228:                                                                          
    ## 229:                                                                          
    ## 230:                                                                          
    ## 231:                                                                          
    ##      responseElements._return responseElements.account
    ##   1:                       NA                       NA
    ##   2:                       NA                       NA
    ##   3:                       NA                       NA
    ##   4:                       NA                       NA
    ##   5:                       NA                       NA
    ##  ---                                                  
    ## 227:                       NA                       NA
    ## 228:                       NA                       NA
    ## 229:                       NA                       NA
    ## 230:                       NA                       NA
    ## 231:                       NA                       NA
    ##      responseElements.alarms{}.alarmARN responseElements.alarms{}.alarmName
    ##   1:                                                                       
    ##   2:                                                                       
    ##   3:                                                                       
    ##   4:                                                                       
    ##   5:                                                                       
    ##  ---                                                                       
    ## 227:                                                                       
    ## 228:                                                                       
    ## 229:                                                                       
    ## 230:                                                                       
    ## 231:                                                                       
    ##      responseElements.arn
    ##   1:                     
    ##   2:                     
    ##   3:                     
    ##   4:                     
    ##   5:                     
    ##  ---                     
    ## 227:                     
    ## 228:                     
    ## 229:                     
    ## 230:                     
    ## 231:                     
    ##      responseElements.complianceSummary.complianceSummaryTimestamp
    ##   1:                                                              
    ##   2:                                                              
    ##   3:                                                              
    ##   4:                                                              
    ##   5:                                                              
    ##  ---                                                              
    ## 227:                                                              
    ## 228:                                                              
    ## 229:                                                              
    ## 230:                                                              
    ## 231:                                                              
    ##      responseElements.complianceSummary.compliantResourceCount.capExceeded
    ##   1:                                                                    NA
    ##   2:                                                                    NA
    ##   3:                                                                    NA
    ##   4:                                                                    NA
    ##   5:                                                                    NA
    ##  ---                                                                      
    ## 227:                                                                    NA
    ## 228:                                                                    NA
    ## 229:                                                                    NA
    ## 230:                                                                    NA
    ## 231:                                                                    NA
    ##      responseElements.complianceSummary.compliantResourceCount.cappedCount
    ##   1:                                                                    NA
    ##   2:                                                                    NA
    ##   3:                                                                    NA
    ##   4:                                                                    NA
    ##   5:                                                                    NA
    ##  ---                                                                      
    ## 227:                                                                    NA
    ## 228:                                                                    NA
    ## 229:                                                                    NA
    ## 230:                                                                    NA
    ## 231:                                                                    NA
    ##      responseElements.complianceSummary.nonCompliantResourceCount.capExceeded
    ##   1:                                                                       NA
    ##   2:                                                                       NA
    ##   3:                                                                       NA
    ##   4:                                                                       NA
    ##   5:                                                                       NA
    ##  ---                                                                         
    ## 227:                                                                       NA
    ## 228:                                                                       NA
    ## 229:                                                                       NA
    ## 230:                                                                       NA
    ## 231:                                                                       NA
    ##      responseElements.complianceSummary.nonCompliantResourceCount.cappedCount
    ##   1:                                                                       NA
    ##   2:                                                                       NA
    ##   3:                                                                       NA
    ##   4:                                                                       NA
    ##   5:                                                                       NA
    ##  ---                                                                         
    ## 227:                                                                       NA
    ## 228:                                                                       NA
    ## 229:                                                                       NA
    ## 230:                                                                       NA
    ## 231:                                                                       NA
    ##      responseElements.configRulesEvaluationStatus{}.configRuleArn
    ##   1:                                                             
    ##   2:                                                             
    ##   3:                                                             
    ##   4:                                                             
    ##   5:                                                             
    ##  ---                                                             
    ## 227:                                                             
    ## 228:                                                             
    ## 229:                                                             
    ## 230:                                                             
    ## 231:                                                             
    ##      responseElements.configRulesEvaluationStatus{}.configRuleId
    ##   1:                                                            
    ##   2:                                                            
    ##   3:                                                            
    ##   4:                                                            
    ##   5:                                                            
    ##  ---                                                            
    ## 227:                                                            
    ## 228:                                                            
    ## 229:                                                            
    ## 230:                                                            
    ## 231:                                                            
    ##      responseElements.configRulesEvaluationStatus{}.configRuleName
    ##   1:                                                              
    ##   2:                                                              
    ##   3:                                                              
    ##   4:                                                              
    ##   5:                                                              
    ##  ---                                                              
    ## 227:                                                              
    ## 228:                                                              
    ## 229:                                                              
    ## 230:                                                              
    ## 231:                                                              
    ##      responseElements.configRulesEvaluationStatus{}.firstActivatedTime
    ##   1:                                                                  
    ##   2:                                                                  
    ##   3:                                                                  
    ##   4:                                                                  
    ##   5:                                                                  
    ##  ---                                                                  
    ## 227:                                                                  
    ## 228:                                                                  
    ## 229:                                                                  
    ## 230:                                                                  
    ## 231:                                                                  
    ##      responseElements.configRulesEvaluationStatus{}.firstEvaluationStarted
    ##   1:                                                                    NA
    ##   2:                                                                    NA
    ##   3:                                                                    NA
    ##   4:                                                                    NA
    ##   5:                                                                    NA
    ##  ---                                                                      
    ## 227:                                                                    NA
    ## 228:                                                                    NA
    ## 229:                                                                    NA
    ## 230:                                                                    NA
    ## 231:                                                                    NA
    ##      responseElements.configRulesEvaluationStatus{}.lastSuccessfulEvaluationTime
    ##   1:                                                                            
    ##   2:                                                                            
    ##   3:                                                                            
    ##   4:                                                                            
    ##   5:                                                                            
    ##  ---                                                                            
    ## 227:                                                                            
    ## 228:                                                                            
    ## 229:                                                                            
    ## 230:                                                                            
    ## 231:                                                                            
    ##      responseElements.configRulesEvaluationStatus{}.lastSuccessfulInvocationTime
    ##   1:                                                                            
    ##   2:                                                                            
    ##   3:                                                                            
    ##   4:                                                                            
    ##   5:                                                                            
    ##  ---                                                                            
    ## 227:                                                                            
    ## 228:                                                                            
    ## 229:                                                                            
    ## 230:                                                                            
    ## 231:                                                                            
    ##      responseElements.configRules{}.configRuleArn
    ##   1:                                             
    ##   2:                                             
    ##   3:                                             
    ##   4:                                             
    ##   5:                                             
    ##  ---                                             
    ## 227:                                             
    ## 228:                                             
    ## 229:                                             
    ## 230:                                             
    ## 231:                                             
    ##      responseElements.configRules{}.configRuleId
    ##   1:                                            
    ##   2:                                            
    ##   3:                                            
    ##   4:                                            
    ##   5:                                            
    ##  ---                                            
    ## 227:                                            
    ## 228:                                            
    ## 229:                                            
    ## 230:                                            
    ## 231:                                            
    ##      responseElements.configRules{}.configRuleName
    ##   1:                                              
    ##   2:                                              
    ##   3:                                              
    ##   4:                                              
    ##   5:                                              
    ##  ---                                              
    ## 227:                                              
    ## 228:                                              
    ## 229:                                              
    ## 230:                                              
    ## 231:                                              
    ##      responseElements.configRules{}.configRuleState
    ##   1:                                               
    ##   2:                                               
    ##   3:                                               
    ##   4:                                               
    ##   5:                                               
    ##  ---                                               
    ## 227:                                               
    ## 228:                                               
    ## 229:                                               
    ## 230:                                               
    ## 231:                                               
    ##      responseElements.configRules{}.description
    ##   1:                                           
    ##   2:                                           
    ##   3:                                           
    ##   4:                                           
    ##   5:                                           
    ##  ---                                           
    ## 227:                                           
    ## 228:                                           
    ## 229:                                           
    ## 230:                                           
    ## 231:                                           
    ##      responseElements.configRules{}.inputParameters
    ##   1:                                               
    ##   2:                                               
    ##   3:                                               
    ##   4:                                               
    ##   5:                                               
    ##  ---                                               
    ## 227:                                               
    ## 228:                                               
    ## 229:                                               
    ## 230:                                               
    ## 231:                                               
    ##      responseElements.configRules{}.maximumExecutionFrequency
    ##   1:                                                         
    ##   2:                                                         
    ##   3:                                                         
    ##   4:                                                         
    ##   5:                                                         
    ##  ---                                                         
    ## 227:                                                         
    ## 228:                                                         
    ## 229:                                                         
    ## 230:                                                         
    ## 231:                                                         
    ##      responseElements.configRules{}.scope.complianceResourceTypes{}
    ##   1:                                                               
    ##   2:                                                               
    ##   3:                                                               
    ##   4:                                                               
    ##   5:                                                               
    ##  ---                                                               
    ## 227:                                                               
    ## 228:                                                               
    ## 229:                                                               
    ## 230:                                                               
    ## 231:                                                               
    ##      responseElements.configRules{}.source.owner
    ##   1:                                            
    ##   2:                                            
    ##   3:                                            
    ##   4:                                            
    ##   5:                                            
    ##  ---                                            
    ## 227:                                            
    ## 228:                                            
    ## 229:                                            
    ## 230:                                            
    ## 231:                                            
    ##      responseElements.configRules{}.source.sourceIdentifier
    ##   1:                                                       
    ##   2:                                                       
    ##   3:                                                       
    ##   4:                                                       
    ##   5:                                                       
    ##  ---                                                       
    ## 227:                                                       
    ## 228:                                                       
    ## 229:                                                       
    ## 230:                                                       
    ## 231:                                                       
    ##      responseElements.credentials.accessKeyId
    ##   1:                                         
    ##   2:                                         
    ##   3:                                         
    ##   4:                                         
    ##   5:                                         
    ##  ---                                         
    ## 227:                                         
    ## 228:                                         
    ## 229:                                         
    ## 230:                                         
    ## 231:                                         
    ##      responseElements.credentials.expiration
    ##   1:                                        
    ##   2:                                        
    ##   3:                                        
    ##   4:                                        
    ##   5:                                        
    ##  ---                                        
    ## 227:                                        
    ## 228:                                        
    ## 229:                                        
    ## 230:                                        
    ## 231:                                        
    ##      responseElements.credentials.sessionToken
    ##   1:                                          
    ##   2:                                          
    ##   3:                                          
    ##   4:                                          
    ##   5:                                          
    ##  ---                                          
    ## 227:                                          
    ## 228:                                          
    ## 229:                                          
    ## 230:                                          
    ## 231:                                          
    ##      responseElements.evaluationResults{}.annotation
    ##   1:                                                
    ##   2:                                                
    ##   3:                                                
    ##   4:                                                
    ##   5:                                                
    ##  ---                                                
    ## 227:                                                
    ## 228:                                                
    ## 229:                                                
    ## 230:                                                
    ## 231:                                                
    ##      responseElements.evaluationResults{}.complianceType
    ##   1:                                                    
    ##   2:                                                    
    ##   3:                                                    
    ##   4:                                                    
    ##   5:                                                    
    ##  ---                                                    
    ## 227:                                                    
    ## 228:                                                    
    ## 229:                                                    
    ## 230:                                                    
    ## 231:                                                    
    ##      responseElements.evaluationResults{}.configRuleInvokedTime
    ##   1:                                                           
    ##   2:                                                           
    ##   3:                                                           
    ##   4:                                                           
    ##   5:                                                           
    ##  ---                                                           
    ## 227:                                                           
    ## 228:                                                           
    ## 229:                                                           
    ## 230:                                                           
    ## 231:                                                           
    ##      responseElements.evaluationResults{}.evaluationResultIdentifier.evaluationResultQualifier.configRuleName
    ##   1:                                                                                                         
    ##   2:                                                                                                         
    ##   3:                                                                                                         
    ##   4:                                                                                                         
    ##   5:                                                                                                         
    ##  ---                                                                                                         
    ## 227:                                                                                                         
    ## 228:                                                                                                         
    ## 229:                                                                                                         
    ## 230:                                                                                                         
    ## 231:                                                                                                         
    ##      responseElements.evaluationResults{}.evaluationResultIdentifier.evaluationResultQualifier.resourceId
    ##   1:                                                                                                     
    ##   2:                                                                                                     
    ##   3:                                                                                                     
    ##   4:                                                                                                     
    ##   5:                                                                                                     
    ##  ---                                                                                                     
    ## 227:                                                                                                     
    ## 228:                                                                                                     
    ## 229:                                                                                                     
    ## 230:                                                                                                     
    ## 231:                                                                                                     
    ##      responseElements.evaluationResults{}.evaluationResultIdentifier.evaluationResultQualifier.resourceType
    ##   1:                                                                                                       
    ##   2:                                                                                                       
    ##   3:                                                                                                       
    ##   4:                                                                                                       
    ##   5:                                                                                                       
    ##  ---                                                                                                       
    ## 227:                                                                                                       
    ## 228:                                                                                                       
    ## 229:                                                                                                       
    ## 230:                                                                                                       
    ## 231:                                                                                                       
    ##      responseElements.evaluationResults{}.evaluationResultIdentifier.orderingTimestamp
    ##   1:                                                                                  
    ##   2:                                                                                  
    ##   3:                                                                                  
    ##   4:                                                                                  
    ##   5:                                                                                  
    ##  ---                                                                                  
    ## 227:                                                                                  
    ## 228:                                                                                  
    ## 229:                                                                                  
    ## 230:                                                                                  
    ## 231:                                                                                  
    ##      responseElements.evaluationResults{}.resultRecordedTime
    ##   1:                                                        
    ##   2:                                                        
    ##   3:                                                        
    ##   4:                                                        
    ##   5:                                                        
    ##  ---                                                        
    ## 227:                                                        
    ## 228:                                                        
    ## 229:                                                        
    ## 230:                                                        
    ## 231:                                                        
    ##      responseElements.instancesSet.items{}.currentState.code
    ##   1:                                                        
    ##   2:                                                        
    ##   3:                                                        
    ##   4:                                                        
    ##   5:                                                        
    ##  ---                                                        
    ## 227:                                                        
    ## 228:                                                        
    ## 229:                                                        
    ## 230:                                                        
    ## 231:                                                        
    ##      responseElements.instancesSet.items{}.currentState.name
    ##   1:                                                        
    ##   2:                                                        
    ##   3:                                                        
    ##   4:                                                        
    ##   5:                                                        
    ##  ---                                                        
    ## 227:                                                        
    ## 228:                                                        
    ## 229:                                                        
    ## 230:                                                        
    ## 231:                                                        
    ##      responseElements.instancesSet.items{}.instanceId
    ##   1:                                                 
    ##   2:                                                 
    ##   3:                                                 
    ##   4:                                                 
    ##   5:                                                 
    ##  ---                                                 
    ## 227:                                                 
    ## 228:                                                 
    ## 229:                                                 
    ## 230:                                                 
    ## 231:                                                 
    ##      responseElements.instancesSet.items{}.previousState.code
    ##   1:                                                         
    ##   2:                                                         
    ##   3:                                                         
    ##   4:                                                         
    ##   5:                                                         
    ##  ---                                                         
    ## 227:                                                         
    ## 228:                                                         
    ## 229:                                                         
    ## 230:                                                         
    ## 231:                                                         
    ##      responseElements.instancesSet.items{}.previousState.name
    ##   1:                                                         
    ##   2:                                                         
    ##   3:                                                         
    ##   4:                                                         
    ##   5:                                                         
    ##  ---                                                         
    ## 227:                                                         
    ## 228:                                                         
    ## 229:                                                         
    ## 230:                                                         
    ## 231:                                                         
    ##      responseElements.isTruncated
    ##   1:                           NA
    ##   2:                           NA
    ##   3:                           NA
    ##   4:                           NA
    ##   5:                           NA
    ##  ---                             
    ## 227:                           NA
    ## 228:                           NA
    ## 229:                           NA
    ## 230:                           NA
    ## 231:                           NA
    ##      responseElements.listeners{}.defaultActions{}.targetGroupArn
    ##   1:                                                             
    ##   2:                                                             
    ##   3:                                                             
    ##   4:                                                             
    ##   5:                                                             
    ##  ---                                                             
    ## 227:                                                             
    ## 228:                                                             
    ## 229:                                                             
    ## 230:                                                             
    ## 231:                                                             
    ##      responseElements.listeners{}.defaultActions{}.type
    ##   1:                                                   
    ##   2:                                                   
    ##   3:                                                   
    ##   4:                                                   
    ##   5:                                                   
    ##  ---                                                   
    ## 227:                                                   
    ## 228:                                                   
    ## 229:                                                   
    ## 230:                                                   
    ## 231:                                                   
    ##      responseElements.listeners{}.listenerArn
    ##   1:                                         
    ##   2:                                         
    ##   3:                                         
    ##   4:                                         
    ##   5:                                         
    ##  ---                                         
    ## 227:                                         
    ## 228:                                         
    ## 229:                                         
    ## 230:                                         
    ## 231:                                         
    ##      responseElements.listeners{}.loadBalancerArn
    ##   1:                                             
    ##   2:                                             
    ##   3:                                             
    ##   4:                                             
    ##   5:                                             
    ##  ---                                             
    ## 227:                                             
    ## 228:                                             
    ## 229:                                             
    ## 230:                                             
    ## 231:                                             
    ##      responseElements.listeners{}.port responseElements.listeners{}.protocol
    ##   1:                                NA                                      
    ##   2:                                NA                                      
    ##   3:                                NA                                      
    ##   4:                                NA                                      
    ##   5:                                NA                                      
    ##  ---                                                                        
    ## 227:                                NA                                      
    ## 228:                                NA                                      
    ## 229:                                NA                                      
    ## 230:                                NA                                      
    ## 231:                                NA                                      
    ##      responseElements.loadBalancers{}.availabilityZones{}.subnetId
    ##   1:                                                              
    ##   2:                                                              
    ##   3:                                                              
    ##   4:                                                              
    ##   5:                                                              
    ##  ---                                                              
    ## 227:                                                              
    ## 228:                                                              
    ## 229:                                                              
    ## 230:                                                              
    ## 231:                                                              
    ##      responseElements.loadBalancers{}.availabilityZones{}.zoneName
    ##   1:                                                              
    ##   2:                                                              
    ##   3:                                                              
    ##   4:                                                              
    ##   5:                                                              
    ##  ---                                                              
    ## 227:                                                              
    ## 228:                                                              
    ## 229:                                                              
    ## 230:                                                              
    ## 231:                                                              
    ##      responseElements.loadBalancers{}.canonicalHostedZoneId
    ##   1:                                                       
    ##   2:                                                       
    ##   3:                                                       
    ##   4:                                                       
    ##   5:                                                       
    ##  ---                                                       
    ## 227:                                                       
    ## 228:                                                       
    ## 229:                                                       
    ## 230:                                                       
    ## 231:                                                       
    ##      responseElements.loadBalancers{}.createdTime
    ##   1:                                             
    ##   2:                                             
    ##   3:                                             
    ##   4:                                             
    ##   5:                                             
    ##  ---                                             
    ## 227:                                             
    ## 228:                                             
    ## 229:                                             
    ## 230:                                             
    ## 231:                                             
    ##      responseElements.loadBalancers{}.dNSName
    ##   1:                                         
    ##   2:                                         
    ##   3:                                         
    ##   4:                                         
    ##   5:                                         
    ##  ---                                         
    ## 227:                                         
    ## 228:                                         
    ## 229:                                         
    ## 230:                                         
    ## 231:                                         
    ##      responseElements.loadBalancers{}.ipAddressType
    ##   1:                                               
    ##   2:                                               
    ##   3:                                               
    ##   4:                                               
    ##   5:                                               
    ##  ---                                               
    ## 227:                                               
    ## 228:                                               
    ## 229:                                               
    ## 230:                                               
    ## 231:                                               
    ##      responseElements.loadBalancers{}.loadBalancerArn
    ##   1:                                                 
    ##   2:                                                 
    ##   3:                                                 
    ##   4:                                                 
    ##   5:                                                 
    ##  ---                                                 
    ## 227:                                                 
    ## 228:                                                 
    ## 229:                                                 
    ## 230:                                                 
    ## 231:                                                 
    ##      responseElements.loadBalancers{}.loadBalancerName
    ##   1:                                                  
    ##   2:                                                  
    ##   3:                                                  
    ##   4:                                                  
    ##   5:                                                  
    ##  ---                                                  
    ## 227:                                                  
    ## 228:                                                  
    ## 229:                                                  
    ## 230:                                                  
    ## 231:                                                  
    ##      responseElements.loadBalancers{}.scheme
    ##   1:                                        
    ##   2:                                        
    ##   3:                                        
    ##   4:                                        
    ##   5:                                        
    ##  ---                                        
    ## 227:                                        
    ## 228:                                        
    ## 229:                                        
    ## 230:                                        
    ## 231:                                        
    ##      responseElements.loadBalancers{}.securityGroups{}
    ##   1:                                                  
    ##   2:                                                  
    ##   3:                                                  
    ##   4:                                                  
    ##   5:                                                  
    ##  ---                                                  
    ## 227:                                                  
    ## 228:                                                  
    ## 229:                                                  
    ## 230:                                                  
    ## 231:                                                  
    ##      responseElements.loadBalancers{}.state.code
    ##   1:                                            
    ##   2:                                            
    ##   3:                                            
    ##   4:                                            
    ##   5:                                            
    ##  ---                                            
    ## 227:                                            
    ## 228:                                            
    ## 229:                                            
    ## 230:                                            
    ## 231:                                            
    ##      responseElements.loadBalancers{}.type
    ##   1:                                      
    ##   2:                                      
    ##   3:                                      
    ##   4:                                      
    ##   5:                                      
    ##  ---                                      
    ## 227:                                      
    ## 228:                                      
    ## 229:                                      
    ## 230:                                      
    ## 231:                                      
    ##      responseElements.loadBalancers{}.vpcId responseElements.nextToken
    ##   1:                                                                  
    ##   2:                                                                  
    ##   3:                                                                  
    ##   4:                                                                  
    ##   5:                                                                  
    ##  ---                                                                  
    ## 227:                                                                  
    ## 228:                                                                  
    ## 229:                                                                  
    ## 230:                                                                  
    ## 231:                                                                  
    ##      responseElements.policyARN responseElements.requestId
    ##   1:                                                      
    ##   2:                                                      
    ##   3:                                                      
    ##   4:                                                      
    ##   5:                                                      
    ##  ---                                                      
    ## 227:                                                      
    ## 228:                                                      
    ## 229:                                                      
    ## 230:                                                      
    ## 231:                                                      
    ##      responseElements.tagDescriptions{}.resourceArn
    ##   1:                                               
    ##   2:                                               
    ##   3:                                               
    ##   4:                                               
    ##   5:                                               
    ##  ---                                               
    ## 227:                                               
    ## 228:                                               
    ## 229:                                               
    ## 230:                                               
    ## 231:                                               
    ##      responseElements.targetGroups{}.healthCheckIntervalSeconds
    ##   1:                                                         NA
    ##   2:                                                         NA
    ##   3:                                                         NA
    ##   4:                                                         NA
    ##   5:                                                         NA
    ##  ---                                                           
    ## 227:                                                         NA
    ## 228:                                                         NA
    ## 229:                                                         NA
    ## 230:                                                         NA
    ## 231:                                                         NA
    ##      responseElements.targetGroups{}.healthCheckPath
    ##   1:                                                
    ##   2:                                                
    ##   3:                                                
    ##   4:                                                
    ##   5:                                                
    ##  ---                                                
    ## 227:                                                
    ## 228:                                                
    ## 229:                                                
    ## 230:                                                
    ## 231:                                                
    ##      responseElements.targetGroups{}.healthCheckPort
    ##   1:                                                
    ##   2:                                                
    ##   3:                                                
    ##   4:                                                
    ##   5:                                                
    ##  ---                                                
    ## 227:                                                
    ## 228:                                                
    ## 229:                                                
    ## 230:                                                
    ## 231:                                                
    ##      responseElements.targetGroups{}.healthCheckProtocol
    ##   1:                                                    
    ##   2:                                                    
    ##   3:                                                    
    ##   4:                                                    
    ##   5:                                                    
    ##  ---                                                    
    ## 227:                                                    
    ## 228:                                                    
    ## 229:                                                    
    ## 230:                                                    
    ## 231:                                                    
    ##      responseElements.targetGroups{}.healthCheckTimeoutSeconds
    ##   1:                                                        NA
    ##   2:                                                        NA
    ##   3:                                                        NA
    ##   4:                                                        NA
    ##   5:                                                        NA
    ##  ---                                                          
    ## 227:                                                        NA
    ## 228:                                                        NA
    ## 229:                                                        NA
    ## 230:                                                        NA
    ## 231:                                                        NA
    ##      responseElements.targetGroups{}.healthyThresholdCount
    ##   1:                                                    NA
    ##   2:                                                    NA
    ##   3:                                                    NA
    ##   4:                                                    NA
    ##   5:                                                    NA
    ##  ---                                                      
    ## 227:                                                    NA
    ## 228:                                                    NA
    ## 229:                                                    NA
    ## 230:                                                    NA
    ## 231:                                                    NA
    ##      responseElements.targetGroups{}.loadBalancerArns{}
    ##   1:                                                   
    ##   2:                                                   
    ##   3:                                                   
    ##   4:                                                   
    ##   5:                                                   
    ##  ---                                                   
    ## 227:                                                   
    ## 228:                                                   
    ## 229:                                                   
    ## 230:                                                   
    ## 231:                                                   
    ##      responseElements.targetGroups{}.matcher.httpCode
    ##   1:                                               NA
    ##   2:                                               NA
    ##   3:                                               NA
    ##   4:                                               NA
    ##   5:                                               NA
    ##  ---                                                 
    ## 227:                                               NA
    ## 228:                                               NA
    ## 229:                                               NA
    ## 230:                                               NA
    ## 231:                                               NA
    ##      responseElements.targetGroups{}.port
    ##   1:                                   NA
    ##   2:                                   NA
    ##   3:                                   NA
    ##   4:                                   NA
    ##   5:                                   NA
    ##  ---                                     
    ## 227:                                   NA
    ## 228:                                   NA
    ## 229:                                   NA
    ## 230:                                   NA
    ## 231:                                   NA
    ##      responseElements.targetGroups{}.protocol
    ##   1:                                         
    ##   2:                                         
    ##   3:                                         
    ##   4:                                         
    ##   5:                                         
    ##  ---                                         
    ## 227:                                         
    ## 228:                                         
    ## 229:                                         
    ## 230:                                         
    ## 231:                                         
    ##      responseElements.targetGroups{}.targetGroupArn
    ##   1:                                               
    ##   2:                                               
    ##   3:                                               
    ##   4:                                               
    ##   5:                                               
    ##  ---                                               
    ## 227:                                               
    ## 228:                                               
    ## 229:                                               
    ## 230:                                               
    ## 231:                                               
    ##      responseElements.targetGroups{}.targetGroupName
    ##   1:                                                
    ##   2:                                                
    ##   3:                                                
    ##   4:                                                
    ##   5:                                                
    ##  ---                                                
    ## 227:                                                
    ## 228:                                                
    ## 229:                                                
    ## 230:                                                
    ## 231:                                                
    ##      responseElements.targetGroups{}.targetType
    ##   1:                                           
    ##   2:                                           
    ##   3:                                           
    ##   4:                                           
    ##   5:                                           
    ##  ---                                           
    ## 227:                                           
    ## 228:                                           
    ## 229:                                           
    ## 230:                                           
    ## 231:                                           
    ##      responseElements.targetGroups{}.unhealthyThresholdCount
    ##   1:                                                      NA
    ##   2:                                                      NA
    ##   3:                                                      NA
    ##   4:                                                      NA
    ##   5:                                                      NA
    ##  ---                                                        
    ## 227:                                                      NA
    ## 228:                                                      NA
    ## 229:                                                      NA
    ## 230:                                                      NA
    ## 231:                                                      NA
    ##      responseElements.targetGroups{}.vpcId
    ##   1:                                      
    ##   2:                                      
    ##   3:                                      
    ##   4:                                      
    ##   5:                                      
    ##  ---                                      
    ## 227:                                      
    ## 228:                                      
    ## 229:                                      
    ## 230:                                      
    ## 231:                                      
    ##      responseElements.targetHealthDescriptions{}.healthCheckPort
    ##   1:                                                            
    ##   2:                                                            
    ##   3:                                                            
    ##   4:                                                            
    ##   5:                                                            
    ##  ---                                                            
    ## 227:                                                            
    ## 228:                                                            
    ## 229:                                                            
    ## 230:                                                            
    ## 231:                                                            
    ##      responseElements.targetHealthDescriptions{}.target.id
    ##   1:                                                      
    ##   2:                                                      
    ##   3:                                                      
    ##   4:                                                      
    ##   5:                                                      
    ##  ---                                                      
    ## 227:                                                      
    ## 228:                                                      
    ## 229:                                                      
    ## 230:                                                      
    ## 231:                                                      
    ##      responseElements.targetHealthDescriptions{}.target.port
    ##   1:                                                        
    ##   2:                                                        
    ##   3:                                                        
    ##   4:                                                        
    ##   5:                                                        
    ##  ---                                                        
    ## 227:                                                        
    ## 228:                                                        
    ## 229:                                                        
    ## 230:                                                        
    ## 231:                                                        
    ##      responseElements.targetHealthDescriptions{}.targetHealth.description
    ##   1:                                                                     
    ##   2:                                                                     
    ##   3:                                                                     
    ##   4:                                                                     
    ##   5:                                                                     
    ##  ---                                                                     
    ## 227:                                                                     
    ## 228:                                                                     
    ## 229:                                                                     
    ## 230:                                                                     
    ## 231:                                                                     
    ##      responseElements.targetHealthDescriptions{}.targetHealth.reason
    ##   1:                                                                
    ##   2:                                                                
    ##   3:                                                                
    ##   4:                                                                
    ##   5:                                                                
    ##  ---                                                                
    ## 227:                                                                
    ## 228:                                                                
    ## 229:                                                                
    ## 230:                                                                
    ## 231:                                                                
    ##      responseElements.targetHealthDescriptions{}.targetHealth.state
    ##   1:                                                               
    ##   2:                                                               
    ##   3:                                                               
    ##   4:                                                               
    ##   5:                                                               
    ##  ---                                                               
    ## 227:                                                               
    ## 228:                                                               
    ## 229:                                                               
    ## 230:                                                               
    ## 231:                                                               
    ##      responseElements.userId
    ##   1:                        
    ##   2:                        
    ##   3:                        
    ##   4:                        
    ##   5:                        
    ##  ---                        
    ## 227:                        
    ## 228:                        
    ## 229:                        
    ## 230:                        
    ## 231:                        
    ##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    result
    ##   1:     You are not authorized to perform this operation. Encoded authorization failure message: uykWYUN6uvr3OwfLSaCrx4YMob1sBEsT8yeDdgdvkZP7xcMXK6I67bM1N1Vc1xN-WLXd2b7WHEuAeJi88cvw4KHlqJDgxaZtnKOnncASYCfV57N1awT4oyomOm4c6pxpRlVXezUZt4KcBBqc2cQK6n9bfVEv8d8cmYjPaRlJCmNB63iwcQy-nuiCdONOY9WpdB4usRJAl0Z3j7956GfIT8GYKkjk6fGYCpdaBQm2iQpbXE0DE2jNlz3DUaRZpDnw5wqMTM0KaxdNkbDJUGCLYhlfLGiDq5JMox36XNuCfzI5LqPE-SYHXQR3cir-hdHyaCgtJvI91JxhZpepcf6sfi9ZWYF5yFEg_k_Ng2v-xbzTsEflkCMalMyaeg97kaoPJgC5GXDcnopixoJv1N2s-49Z_ot7Yz2wTPxdNc_4ZzceYHQcmS9InxNYQPvYdRS7iS4uHWqUOVC3CZDhxfaOJX26qL5fb4wyVM6pCX0uewXYGozI231M-a0oLOHHi6fdvXOseD6Nu3SO8LNdayxKoT7fAi63bhK9UuLBU6SWahOubvCctQG3PLiP_GkXT5c84Vnkg-3VLPoWWnT5M_CEV49V1_td7Bti7oLbmN4rcmJoLVS3ZaSfZmqp35-DMZpQXlWoee8glQbckUY15C0Wf1ODUqZybmPO_z3fb-U
    ##   2:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    You are not authorized to perform this operation.
    ##   3:      You are not authorized to perform this operation. Encoded authorization failure message: soDmUbPRC4O4yAsu0JTVTJNwNsmaZleYXO_6pWpOxnTMqx45nKwgOj2e5XMlZjTtY0IjW1O-m5y6bz3S1PbtlZWa1qeuWnoJO6rN_JxWz3RGMk7ZJXSI97bctGyTRtI_08xye2TbjcUEz8eEBWiF4zjE59zqkiievq1jMZ3LLTtp6KCOyl8Z-RbthZnr7uBi7rfSiYGWJ26bYn7lrCQGdUAWzqjd4xfy8Vzwm6rxzVx2s6jeGAo0O4CfWw2hjfbF6Go3AsyJVnE39GV3OfC1IjMJ4Zlo0xNKlXHtdzP7eVLQZEO5WaFmJqI9WdIRC-JtRTRfJXckN4aqT_jEDwvxCmJr7m99WeZnjvvyQkO4AjerZB-xUQzyynTYPf_l-efeenAPGFCOK1_bdj46gwOrheiT_rRXsJagQK3rx3txrE2EvepXGyMx12GYdqA9SdqOTi2Ch37x7UbpUXPo6wZ4tcz1uPMjiOuFA-OwYLDt-urXSjDt3SrDgWWhpQbRUriYMyW90JjHgw7VmG-rVHEqLo-9dzbq7ua4gVoaQzVbUdy5UuFEClUCqTKQESfXJ0cQtb5_isphm2RNRtO1Bxe4DLJaKDnjQQuJn8rEMmMvWPIh68PkhFLNw8fjXoZg9BAECAvgNEfBu9qac4gHdFq-W-D1KylHYVxdBRhvcA
    ##   4:     You are not authorized to perform this operation. Encoded authorization failure message: V8oNUk1OFBOj_y6MC-ZFHiHGltuaCn7-Oejei6g9cSshkFnOREh-iZMO3EK2deoKvzRDdWS4GC5oH8CDKpJjdQ9RMjzBpUrGPzu-CJsdhsJp9XZklx3TOjykmTLhDakW656yb-6AjCY5U65eC_PYhM8JPE2l45HM1sf8j4xrcTSSO_uzeMw-YOncc4DDQx2c3HYM-PZTFeiuwiK2hn-8hFXvVDJlVkP2AWg3t6kLPz8e6ZY_f6uJjzGcXj-8bLwAvTlXqTjDvsSlKlQcFvbVNx13mRvu5GV66ftp8deeSNdREel9qG-p27fMMDgF-YQTMCFflbpIYDENuEIiAuqQGgApSMLrMVMSz9T7zAfEp7IYTlq2a3OjExHrY-kGIfDrmFTrwCKt__b1UywSEot_agf_IFCuEabMzT9wSRIu710MjIz8M0gtHs4wP9kPlHo3a5gDc60YvFURBBd11S2grcelgog36ER9tlf7HvaBHkZWfHxiJneVj34SLHKta1fAGHuaUGCrkkMk45aar7cVv62aStnM6B_mizg4sgBLEC3M_2lFOAIphvHW4ApgLymLtBPdsiGhbQCIRXiNnIYpPGJFKP-evgzAfFBvDt53tDS4kkZvLdh38j-FfhX0h2viQxenEHmsr8zF6jP3LTQPow6lZIcdFHjMMyCjPAs
    ##   5:      You are not authorized to perform this operation. Encoded authorization failure message: sIgNW6SqXz3GgKO7OabL1ieLKRRw_0jjaLtx_JDQiV7TzfaGp0brOE4_RMJl8helfJWu1q95ZYja0xKyohvfF6cjeYqAvZExq069pkuQKREiFrmDQYaHTThINsGfYfRGzVY4VcCbbx99xjXgXIxH1Zu0-y_-gpHrb4_dESwhUCrJKExLA4ddHb_JqmgHtRJj5UGaTlLFYYh_DIF_dVHV5syrgEPYlXFvnypF5XtE9QIY-xZHUCft_BG3NKUPNCtEOoPNK0Wi9Vg9Jn_ty4TdYJiGt5nxULMYvkiQHrCiLZqHEqVjAEqNNDt2W8FTto48WLS09PB3-mQBUi3DnltrVt4IfEwaumDloPbVlkSTBQcMnaNTFTov6LY4whwVxdPy4o6aQsQiIiUH3IZsEBVtZhl9Q-5Xn0jGqnRFHlRY0iMKijON6SAXPvRDjk9WyW4S6aIa6X03W1ON8ZN4sYXCstZLCkcydKsR3Tsapiv6v-NUPA4bFtn6w29aEWCUW_e5GPa17qsKrQwjhZnVL8-ZdZNwU9PppQTz0EQrngcBRmDfbzPU9_Z2tXFClZj9SqARaR2rVnR4siGwc6Fvyu_47OUaUoNV1H22igD-sNmhzKmlw_Rg-4z5pDizbUAFIm3kHK5zYMBPUQXoQhnB-3DoQcBhrbaO4KhcEVx0Ug
    ##  ---                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
    ## 227: You are not authorized to perform this operation. Encoded authorization failure message: sFso9_AhbnX87-4WNPO-4L46kGsRRl6ejlV5PfeDA8K0QQXYMPEfXWeDJLITI9xAPvtmEKd8dDyGk2iEhAruo7GoTbTkUBRXkeqVtU9wvVE_HQaXMFdGX1FOdw6ff9KnCZrLNJOHCmnV_tQnt4V4HhewieshNc3URQ6-jvNMYjTztb9cp8vrE9tjNIkz5j47XN4FR3F-26qPHNgOW582_nYOSv-R1sEQUe6QAcUMaTuMPUVw8pU2xePiAPjs8s9G3ycxyZI3pMXDBXTCP4v1Tu6VR-q0iF9DUG8PBk5vB9_VSH7RUiw9HVfoulhSOx6KIms71VxzmURHKFx2imUUFIgTduBXFfDZV8GGr1diVW8_CDqWqXgIbh-jzDeafYtO66KYSGoGZ-zQlHbHuNo0qFW0_m0geqhdr5LUwgPsDnp_CO_HwFX1ZoWawKYq748peb22SfdWsf-CFRaFOvaZoQjOrCX34aJoO4gKaz0UA-pht4-a7rfxYUJcFzbnXrOOZkOzek0vl3_vMh4hdWRa21rv6j5IFw63HAXA-B6VII93oLO-7pUNBoRnQgnnzKeRL2i_ZpNg5RGfe3DipPVrzKCmjaQnVpPKQCkZs7JdpX8GPvDwcEEVZ1MOdHrX62HGR85SbkB05BorOpcKV8d8kHf7iP7P2tEr80IQsqFjglY
    ## 228: You are not authorized to perform this operation. Encoded authorization failure message: xvZitPBwgPLNwD7syX4l0-Mv3UqLCQleg116nNGCQmXs7g6PcZh3_uGypCE2FiryY-tH1dMTQd31kpWiW3VgJm4XQT_Mhp7hbbsRrDSqp3LnbKxFZy8INHqZ_20Wa_CvsB4I5Jlit1fSvynfwTdXD158hUpkDd7765L2bYO0j5U81D6qRfn7FG5yuLM3sB9Gk9SCQpCohYWT2piA0TUCqGXQ1TjqG5sCsxOnb5ekBUDk5pXB2cLpvw-04gK7Ovbaf1PY8c0zNY9MdyaK9u68gsljBlMyIJMpdF1TqfcIm6e-gQGnbBHnJvFUW1k7D98YhJc2OBO12oRQ7mcsUwm_zqlhFOsujif0-AYthNECskAIx9Pf-Yr1uCgi1wcIZn88zaT-DP-Osrlm5E3uyZPyw9jq-fZ3SgjWGzzKN0A5B83WbpFj_4F71Y6z-fBuDomyYMAgCcU9gChN2-OX1PGJcY7rNWx7Hs39yxNL5s8tuYsttOA7cSsmoPoCnfuH7Ccvy2KH4BaB8Ea0HqTaCr1Negz7PxqpxJnnJd_LJCc5REElC4U2QRD9YAFCtMaCN2BHDd3lswb0i4U2Lp32ypEzpuY8rVXrROrSSTXg3tXzjvLAd8ZU5JueR346hHJ8y3KKekABK7MiD6BbvDvyttHFM1r0W2fs3Kf5xEqP-716LyI
    ## 229:  You are not authorized to perform this operation. Encoded authorization failure message: WkaNGddTeVqgAOdofQBkATAnLtD1czbdXR-MExrUIAezlLVXv8J1Hf_Zi5HO4HmHL77UMeMDgw9-7MoymK-2VzdGW8EB_X8iMhLWYw-6KqDi_n2iumaEvNBA2a9fbUJdoNhUPe88fzU3zhHNJlggYcTMNZOrg1tnkwQAM5aEzoewlRCa8mEcy36HUUed9UxBgQclsibd0V5uNr1garIGoUhQ-yJ_xSXVI51rH7jLpAiUDQlk82dMuIf6cQVwFjpapVqeWS23PF9WnL6eA6lm7W-4FfcPh2sEPDD61V4O8D8a9OMtVkBoYk1ahh7v1Eb-KuMA-k5buyX-unFtkt49qkZOe4bxfEcdxlj_wBleAaay3vgvyYFIptOw02slofRiPufe1wQZGwLPV-KIUnjdUiJ9PPL7-lwAGQL9I1nTKtAQa8wS6K6gV8anOEbkRS3CZJsOxhc8ZZ6Ukr3PLTkSJs9lbrDp76XKblebgi_vNZHpntDKIhtRQs5JOmE3ZONaC-1OHX0e5C5jz_5UxYBx0qqZ3AOc6sPOE45TIjpMLYkERlRovuIx8UHxYczHUUiZD1DdC9h0Is3qv3OhZRfiPVc3XIOykCQ5PNGFz-ej5qkWTancwRX_eKjlmjHnpyevR6CozU7ct4fhVDn1vku7UzwtAOBAhon1OJlUouvtOg
    ## 230: You are not authorized to perform this operation. Encoded authorization failure message: 3lDHOCCsUvr52KUDdk74MpoxaHTr5rOX6Cwb3k7ZbWtA0RsMyARKNK8JAP-7FIx6nzGcDeeMG8Eei5YUbbdKkLdNAvEClAon0qkvOQbr4ofJnjBFsxlQegvg-mo0kQ2YCneyVw-kj4A4E4dUby_zUPyVLyb1_PWTg-OmyMBE3X6V2scEEOrjS0S_7Xk7-2LUbLFH4lgeRn1qAED_MPiSRCmBcKo_SRJ90BC4oB_C6uKTchWl2ZhCitFucYwZBlTTtK7G9rBXj7jyEvIz0QSNwYXW4b4eaTv4nVbI2vN80odXID0HhRSbn-RujsE_B2P_zy4xvWkGZdNiG--PgT54vi0ijIfDkbdfmbsDetJJL4J1_pTkWU7vMV_9XKetFiniorBgzf7tDx8CbCPQWs-0ro0V-rSqIvP7nA341aSkzDRdpP45rno2EzSfwhg7IzsnHbfZ6mzeM50SdHbsl4vnGZEZxsJwgA8OQU-4a4vI4k3sa7bS_SSLva3xRXhIiO4yo7VMvJcoI7SsmKYlj3BI8pWh5UcE2ZzA1DYGmEisYxhb0wTQ_TR17h3WC4MaZRFpZ47Uz1bDA4tidtDvDiaLTwNW1cJGwugThWQ-9QEF-zIzNq6Cz7eNehAqPAZuAQXyg3-8ZijyIp2FSeCbxZ7afEsRmGxL26AmPwPF7egmxaY
    ## 231:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    You are not authorized to perform this operation.
    ##                         result_id                 signature
    ##   1: Client.UnauthorizedOperation              RunInstances
    ##   2: Client.UnauthorizedOperation         DescribeInstances
    ##   3: Client.UnauthorizedOperation              RunInstances
    ##   4: Client.UnauthorizedOperation              RunInstances
    ##   5: Client.UnauthorizedOperation              RunInstances
    ##  ---                                                       
    ## 227: Client.UnauthorizedOperation              RunInstances
    ## 228: Client.UnauthorizedOperation              RunInstances
    ## 229: Client.UnauthorizedOperation              RunInstances
    ## 230: Client.UnauthorizedOperation              RunInstances
    ## 231: Client.UnauthorizedOperation DescribeAccountAttributes
    ##                                                                                                                                                                     source
    ##   1:           s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/eu-west-1/2018/07/26/622676721278_CloudTrail_eu-west-1_20180726T0525Z_ucdqjIisX1gmpotl.json.gz
    ##   2:           s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/eu-west-1/2018/07/26/622676721278_CloudTrail_eu-west-1_20180726T0525Z_ucdqjIisX1gmpotl.json.gz
    ##   3:           s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/eu-west-1/2018/07/26/622676721278_CloudTrail_eu-west-1_20180726T0525Z_ucdqjIisX1gmpotl.json.gz
    ##   4:           s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/eu-west-1/2018/07/26/622676721278_CloudTrail_eu-west-1_20180726T0525Z_ucdqjIisX1gmpotl.json.gz
    ##   5:           s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/eu-west-1/2018/07/26/622676721278_CloudTrail_eu-west-1_20180726T0525Z_ucdqjIisX1gmpotl.json.gz
    ##  ---                                                                                                                                                                      
    ## 227: s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/ap-northeast-2/2018/07/26/622676721278_CloudTrail_ap-northeast-2_20180726T0520Z_j8h0mj1fNX148yKO.json.gz
    ## 228: s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/ap-northeast-2/2018/07/26/622676721278_CloudTrail_ap-northeast-2_20180726T0520Z_j8h0mj1fNX148yKO.json.gz
    ## 229: s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/ap-northeast-2/2018/07/26/622676721278_CloudTrail_ap-northeast-2_20180726T0520Z_j8h0mj1fNX148yKO.json.gz
    ## 230: s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/ap-northeast-2/2018/07/26/622676721278_CloudTrail_ap-northeast-2_20180726T0520Z_j8h0mj1fNX148yKO.json.gz
    ## 231:           s3://cloudtrail-622676721278/AWSLogs/622676721278/CloudTrail/us-east-1/2018/07/26/622676721278_CloudTrail_us-east-1_20180726T0530Z_rEp2EUaBfZcdd5x2.json.gz
    ##      sourceIPAddress     sourcetype   splunk_server splunk_server_group
    ##   1:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ##   2:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ##   3:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ##   4:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ##   5:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ##  ---                                                                   
    ## 227:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ## 228:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ## 229:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ## 230:  139.198.18.205 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ## 231:   82.102.18.111 aws:cloudtrail LAPTOP-UIK62IBC                  NA
    ##                 src         src_ip src_user src_user_id src_user_role
    ##   1: 139.198.18.205 139.198.18.205                                 NA
    ##   2: 139.198.18.205 139.198.18.205                                 NA
    ##   3: 139.198.18.205 139.198.18.205                                 NA
    ##   4: 139.198.18.205 139.198.18.205                                 NA
    ##   5: 139.198.18.205 139.198.18.205                                 NA
    ##  ---                                                                 
    ## 227: 139.198.18.205 139.198.18.205                                 NA
    ## 228: 139.198.18.205 139.198.18.205                                 NA
    ## 229: 139.198.18.205 139.198.18.205                                 NA
    ## 230: 139.198.18.205 139.198.18.205                                 NA
    ## 231:  82.102.18.111  82.102.18.111                                 NA
    ##      src_user_type           start_time  status
    ##   1:            NA 2018-08-20T09:21:05Z failure
    ##   2:            NA 2018-08-20T09:20:26Z        
    ##   3:            NA 2018-08-20T09:20:52Z failure
    ##   4:            NA 2018-08-20T09:20:53Z failure
    ##   5:            NA 2018-08-20T09:21:01Z failure
    ##  ---                                           
    ## 227:            NA 2018-08-20T09:18:40Z failure
    ## 228:            NA 2018-08-20T09:18:43Z failure
    ## 229:            NA 2018-08-20T09:18:44Z failure
    ## 230:            NA 2018-08-20T09:17:48Z failure
    ## 231:            NA 2018-08-20T09:27:06Z        
    ##                                            tag tag::action tag::app
    ##   1:            change\ncloud\nendpoint\nerror                   NA
    ##   2: account\nchange\ncloud\nerror\nmanagement                   NA
    ##   3:            change\ncloud\nendpoint\nerror                   NA
    ##   4:            change\ncloud\nendpoint\nerror                   NA
    ##   5:            change\ncloud\nendpoint\nerror                   NA
    ##  ---                                                               
    ## 227:            change\ncloud\nendpoint\nerror                   NA
    ## 228:            change\ncloud\nendpoint\nerror                   NA
    ## 229:            change\ncloud\nendpoint\nerror                   NA
    ## 230:            change\ncloud\nendpoint\nerror                   NA
    ## 231: account\nchange\ncloud\nerror\nmanagement                   NA
    ##                                 tag::eventtype tag::object_category
    ##   1:            change\ncloud\nendpoint\nerror                   NA
    ##   2: account\nchange\ncloud\nerror\nmanagement                   NA
    ##   3:            change\ncloud\nendpoint\nerror                   NA
    ##   4:            change\ncloud\nendpoint\nerror                   NA
    ##   5:            change\ncloud\nendpoint\nerror                   NA
    ##  ---                                                               
    ## 227:            change\ncloud\nendpoint\nerror                   NA
    ## 228:            change\ncloud\nendpoint\nerror                   NA
    ## 229:            change\ncloud\nendpoint\nerror                   NA
    ## 230:            change\ncloud\nendpoint\nerror                   NA
    ## 231: account\nchange\ncloud\nerror\nmanagement                   NA
    ##      temp_access_key timeendpos timestartpos                  user
    ##   1:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ##   2:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ##   3:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ##   4:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ##   5:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ##  ---                                                              
    ## 227:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ## 228:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ## 229:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ## 230:                         72           52 AIDAJNUCQVD57VVGYEFTQ
    ## 231:                         71           51 AIDAJNUCQVD57VVGYEFTQ
    ##                                                                userAgent
    ##   1: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   2: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   3: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   4: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   5: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##  ---                                                                    
    ## 227: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 228: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 229: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 230: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 231:                                                   ElasticWolf/5.1.6
    ##      userIdentity.accessKeyId userIdentity.accountId
    ##   1:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ##   2:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ##   3:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ##   4:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ##   5:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ##  ---                                                
    ## 227:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ## 228:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ## 229:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ## 230:     ASIAZB6TMXZ7LL6JBJQA               6.23e+11
    ## 231:     AKIAJOGCDXJ5NW5PXUPA               6.23e+11
    ##                              userIdentity.arn userIdentity.invokedBy
    ##   1: arn:aws:iam::622676721278:user/web_admin                       
    ##   2: arn:aws:iam::622676721278:user/web_admin                       
    ##   3: arn:aws:iam::622676721278:user/web_admin                       
    ##   4: arn:aws:iam::622676721278:user/web_admin                       
    ##   5: arn:aws:iam::622676721278:user/web_admin                       
    ##  ---                                                                
    ## 227: arn:aws:iam::622676721278:user/web_admin                       
    ## 228: arn:aws:iam::622676721278:user/web_admin                       
    ## 229: arn:aws:iam::622676721278:user/web_admin                       
    ## 230: arn:aws:iam::622676721278:user/web_admin                       
    ## 231: arn:aws:iam::622676721278:user/web_admin                       
    ##      userIdentity.principalId
    ##   1:    AIDAJNUCQVD57VVGYEFTQ
    ##   2:    AIDAJNUCQVD57VVGYEFTQ
    ##   3:    AIDAJNUCQVD57VVGYEFTQ
    ##   4:    AIDAJNUCQVD57VVGYEFTQ
    ##   5:    AIDAJNUCQVD57VVGYEFTQ
    ##  ---                         
    ## 227:    AIDAJNUCQVD57VVGYEFTQ
    ## 228:    AIDAJNUCQVD57VVGYEFTQ
    ## 229:    AIDAJNUCQVD57VVGYEFTQ
    ## 230:    AIDAJNUCQVD57VVGYEFTQ
    ## 231:    AIDAJNUCQVD57VVGYEFTQ
    ##      userIdentity.sessionContext.attributes.creationDate
    ##   1:                                2018-08-20T09:16:12Z
    ##   2:                                2018-08-20T09:16:12Z
    ##   3:                                2018-08-20T09:16:12Z
    ##   4:                                2018-08-20T09:16:12Z
    ##   5:                                2018-08-20T09:16:12Z
    ##  ---                                                    
    ## 227:                                2018-08-20T09:16:12Z
    ## 228:                                2018-08-20T09:16:12Z
    ## 229:                                2018-08-20T09:16:12Z
    ## 230:                                2018-08-20T09:16:12Z
    ## 231:                                                    
    ##      userIdentity.sessionContext.attributes.mfaAuthenticated userIdentity.type
    ##   1:                                                   FALSE           IAMUser
    ##   2:                                                   FALSE           IAMUser
    ##   3:                                                   FALSE           IAMUser
    ##   4:                                                   FALSE           IAMUser
    ##   5:                                                   FALSE           IAMUser
    ##  ---                                                                          
    ## 227:                                                   FALSE           IAMUser
    ## 228:                                                   FALSE           IAMUser
    ## 229:                                                   FALSE           IAMUser
    ## 230:                                                   FALSE           IAMUser
    ## 231:                                                      NA           IAMUser
    ##      userIdentity.userName  userName      user_access_key
    ##   1:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ##   2:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ##   3:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ##   4:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ##   5:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ##  ---                                                     
    ## 227:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ## 228:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ## 229:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ## 230:             web_admin web_admin ASIAZB6TMXZ7LL6JBJQA
    ## 231:             web_admin web_admin AKIAJOGCDXJ5NW5PXUPA
    ##                                                               user_agent
    ##   1: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   2: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   3: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   4: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##   5: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ##  ---                                                                    
    ## 227: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 228: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 229: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 230: Boto3/1.7.42 Python/2.7.12 Linux/4.4.0-131-generic Botocore/1.10.42
    ## 231:                                                   ElasticWolf/5.1.6
    ##                                      user_arn user_group_id
    ##   1: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ##   2: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ##   3: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ##   4: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ##   5: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ##  ---                                                       
    ## 227: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ## 228: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ## 229: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ## 230: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ## 231: arn:aws:iam::622676721278:user/web_admin      6.23e+11
    ##                    user_id user_role user_type              vendor
    ##   1: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ##   2: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ##   3: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ##   4: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ##   5: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ##  ---                                                              
    ## 227: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ## 228: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ## 229: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ## 230: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ## 231: AIDAJNUCQVD57VVGYEFTQ        NA   IAMUser Amazon Web Services
    ##      vendor_account  vendor_region vpcEndpointId
    ##   1:       6.23e+11      eu-west-1              
    ##   2:       6.23e+11      eu-west-1              
    ##   3:       6.23e+11      eu-west-1              
    ##   4:       6.23e+11      eu-west-1              
    ##   5:       6.23e+11      eu-west-1              
    ##  ---                                            
    ## 227:       6.23e+11 ap-northeast-2              
    ## 228:       6.23e+11 ap-northeast-2              
    ## 229:       6.23e+11 ap-northeast-2              
    ## 230:       6.23e+11 ap-northeast-2              
    ## 231:       6.23e+11      us-east-1

What is the acceptable amount of request a “non malicious” machine
makes?

``` r
#look at distribution for each of the error codes

cloudtrail[, list(eventTime, eventType, errorCode, sourceIPAddress)]
```

    ##                  eventTime  eventType                    errorCode
    ##    1: 2018-08-20T14:53:30Z AwsApiCall                      success
    ##    2: 2018-08-20T14:53:29Z AwsApiCall                      success
    ##    3: 2018-08-20T14:53:29Z AwsApiCall                      success
    ##    4: 2018-08-20T14:53:29Z AwsApiCall                      success
    ##    5: 2018-08-20T14:53:29Z AwsApiCall                      success
    ##   ---                                                             
    ## 5446: 2018-08-20T09:21:53Z AwsApiCall Client.InstanceLimitExceeded
    ## 5447: 2018-08-20T09:21:50Z AwsApiCall           Client.Unsupported
    ## 5448: 2018-08-20T09:22:04Z AwsApiCall           Client.Unsupported
    ## 5449: 2018-08-20T09:21:34Z AwsApiCall Client.InstanceLimitExceeded
    ## 5450: 2018-08-20T09:21:58Z AwsApiCall Client.InstanceLimitExceeded
    ##       sourceIPAddress
    ##    1:   34.215.24.225
    ##    2:   34.215.24.225
    ##    3:   34.215.24.225
    ##    4:   34.215.24.225
    ##    5:   34.215.24.225
    ##   ---                
    ## 5446:  139.198.18.205
    ## 5447:  139.198.18.205
    ## 5448:  139.198.18.205
    ## 5449:  139.198.18.205
    ## 5450:  139.198.18.205

``` r
# how many request per time period? (choose period)

cloudtrail[, eventTime_lubri := ymd_hms(eventTime)]

# We seperate the moment when the login began from the unique ip address out in n_min window 
# For each window we're going to how many logins occured

# 10 min 
# 30 min
# 1 hour
# 2 hour ~


# If this an attack, the time (the lag) betweeen malicious attempts to login would probabaly be much shorter than if a human were doing it, (assuming, the attack is automated through a brute force approach)

cloudtrail[, .N, by = list(eventTime,sourceIPAddress)]
```

    ##                 eventTime sourceIPAddress  N
    ##   1: 2018-08-20T14:53:30Z   34.215.24.225 55
    ##   2: 2018-08-20T14:53:29Z   34.215.24.225 57
    ##   3: 2018-08-20T14:53:39Z   34.215.24.225  9
    ##   4: 2018-08-20T14:53:28Z   34.215.24.225  6
    ##   5: 2018-08-20T14:54:51Z   34.215.24.225  9
    ##  ---                                        
    ## 987: 2018-08-20T09:27:07Z   82.102.18.111  1
    ## 988: 2018-08-20T09:27:06Z   82.102.18.111  1
    ## 989: 2018-08-20T09:21:53Z  139.198.18.205  1
    ## 990: 2018-08-20T09:21:34Z  139.198.18.205  1
    ## 991: 2018-08-20T09:21:58Z  139.198.18.205  1

``` r
counts_async_by_eventime <- cloudtrail[, .N, by = list(eventTime_lubri,sourceIPAddress, eventType, errorCode)]

ggplot(counts_async_by_eventime, aes(x = N) ) +
  geom_density(color = "darkblue", fill = "lightblue") + 
  ggtitle("Density of Requests by Event Time") + 
  xlab("Count of Logins")
```

![](Exploration_Cloudtrail_files/figure-markdown_github/unnamed-chunk-6-1.png)

``` r
density_counts_eventime <- ggplot(counts_async_by_eventime, aes(x = N) ) +
  geom_density(color = "darkblue", fill = "lightblue") + 
  ggtitle("Density of Requests by Event Time") + 
  xlab("Count of Logins")
```

``` r
density_counts_eventime + facet_wrap(eventType~.)
```

![](Exploration_Cloudtrail_files/figure-markdown_github/unnamed-chunk-7-1.png)

``` r
density_counts_eventime + 
  facet_wrap(errorCode~.)
```

    ## Warning: Groups with fewer than two data points have been dropped.

    ## Warning: Groups with fewer than two data points have been dropped.

    ## Warning in max(ids, na.rm = TRUE): no non-missing arguments to max; returning -
    ## Inf

    ## Warning in max(ids, na.rm = TRUE): no non-missing arguments to max; returning -
    ## Inf

![](Exploration_Cloudtrail_files/figure-markdown_github/unnamed-chunk-8-1.png)
