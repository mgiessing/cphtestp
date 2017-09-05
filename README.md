# cphtestp
Environment for creating a docker image running cph performance tests for Persistent messaging.

This repository contains a set of files to help create a Docker image containing the CPH executable.

You will need to seperately download the MQ Client (for which license agreement is required) and copy the following files into the root directory before building your docker image:
* /lap/
*  mqlicense.sh
*  ibmmq-client_9.0.3.0_amd64.deb
*  ibmmq-runtime_9.0.3.0_amd64.deb

The MQ V9 client can be obtained from:
http://www-01.ibm.com/support/docview.wss?uid=swg24042176

then perform a docker build as normal:

`docker build --tag cphtestp .`

then run in network host mode to connect and run tests against a local QM:

`docker run -it --detach --net="host" cphtestp`

The current configuration looks for a local QM called PERF0 with a listener configured on port 1420. You can either edit the scripts to support a different configuration or alter them to utilise environment variables which could be provided in your run command.

The version of cph contained in this image was taken on 4th August 2017 and built on 64bit xLinux. The most up to date cph code can be found here:
https://github.com/ibm-messaging/mq-cph
