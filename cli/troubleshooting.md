## Troubleshooting Guide


### InsecurePlatformWarning

On Centos/Redhat, with Python version 2.7.9 or earlier, if you see the following exception:

`InsecurePlatformWarning: A true SSLContext object is not available. This prevents urllib3 from configuring SSL appropriately and may cause certain SSL connections to fail. For more information, see https://urllib3.readthedocs.org/en/latest/security.html#insecureplatformwarning.`


Try:

`pip install pyopenssl ndg-httpsclient pyasn1`


