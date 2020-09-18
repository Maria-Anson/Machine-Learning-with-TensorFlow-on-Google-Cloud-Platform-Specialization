## Intro to Renting-VM Lab

*****

In this lab you spin up a virtual machine, configure its security, access it
remotely, and then carry out the steps of an ingest-transform-and-publish data
pipeline manually.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/DDYIKwe2Eei89hLHgCiRzA_5b9d09008f6d8de1f6a6e350e08dcbe7_T-HGDML-I_M5_L6_Map.png?expiry=1600560000000&hmac=ovdyx5Gg9HFqSNjoigtwqHHchMj9JsjUHliwR6KtJBg)

The point is to ingest earthquake data from the US Geographic Service and create
a map like the one shown. The map will be inserted into a web page, and then you
will publish that web page. In order to carry out the compute, you will spin up
a virtual machine and access it remotely.  You will install some software on it,
download some scripts, and then run them to do the actual data processing. The
resulting files will be copied to Cloud Storage, from which you can set the
access control to publish the files for anyone to access.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/LE5uZQe2Eei_ZQ6W1G11dA_0a269a5f4fcf341d6cd7b4e890830eee_T-HGDML-I_M5_L6_Steps.png?expiry=1600560000000&hmac=a6SJBe2PSZ6krcjjauKj3Epx41t8wTd-SkzvZITiRbU)

And that’s it—Google Cloud Platform will take care of the rest. Your files will
be globally available and edge-cached so that people halfway across the world
can access them quickly.


