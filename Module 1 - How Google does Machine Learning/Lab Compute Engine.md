###### 25/25

#### Checkpoints

Create Compute Engine instance with the necessary API access 

5 / 5 

Install software 

5 / 5 

Ingest USGS data 

5 / 5 

Transform the data 

5 / 5 

Create bucket and Store data 

5 / 5 



# Rent-a-VM to process earthquake data MLGCP 

## Overview

Using Google Cloud to set up a virtual machine to process earthquake data frees
you from IT minutia to focus on your scientific goals.  You can ingest and
process data, then present the results in various formats. In this lab, you will
ingest real-time earthquake data published by the United States Geological
Survey (USGS) and create maps that look like the following:



In this lab you will spin up a virtual machine, access it remotely, and then
manually create a pipeline to retrieve, process and publish the data.

### What you will learn

In this lab, you will learn how to do the following:

* Create a Compute Engine instance with specific security permissions.
* SSH into the instance.
* Install the software package Git (for source code version control).
* Ingest data into the Compute Engine instance.
* Transform data on the Compute Engine instance.
* Store the transformed data on Cloud Storage.
* Publish Cloud Storage data to the web.

## Setup

For each lab, you get a new Google Cloud project and set of resources for a
fixed time at no cost.

1.  

Make sure you signed into Qwiklabs using an **incognito window**.

1.  

Note the lab's access time (for example,  and make sure you can finish in that
time block.

There is no pause feature. You can restart if needed, but you have to start at
the beginning.   

1.  

When ready, click .

1.  

Note your lab credentials. You will use them to sign in to the Google Cloud
Console. 

1.  

Click **Open Google Console**.

1.  

Click **Use another account** and copy/paste credentials for **this** lab into
the prompts.

If you use other credentials, you'll get errors or **incur charges**.   

1.  Accept the terms and skip the recovery resource page.

Do not click **End Lab** unless you are finished with the lab or want to restart
it. This clears your work and removes the project.   

## Create Compute Engine instance with the necessary API access

To create a Compute Engine instance, from the **Navigation menu** click on
**Compute Engine** > **VM instances**:

Click **Create** and wait for the "Create an instance" form to load:



Use default Region and Zone for creating the instance:



Change Identify and API access for the Compute Engine default service account to
**Allow full access to all Cloud APIs**, then click **Create**.



You'll see a green circle with a check when the instance is created.

Click *Check my progress* to verify the objective. 

## SSH into the instance

You can remotely access your Compute Engine instance using Secure Shell (SSH):

Click the **SSH** button next to your newly created VM:



The VM instance details displays.

SSH keys are automatically transferred; no extra software is needed to ssh
directly from the browser.

To find some information about the Compute Engine instance, type the following
into the command-line:


You should see a similar output:


## Install software

Still in the SSH window, enter the following commands:




Enter **Y** when asked if it's acceptable to use additional disk space.

Verify that git is now installed:


You should see a similar output:


Click *Check my progress* to verify the objective. 

## Ingest USGS data

Still in the SSH window, enter the following command to download the code from
github:


Navigate to the folder corresponding to this lab:


Examine the `ingest` code using `less`:


The `less` command allows you to view the file (Press the **spacebar** to scroll
down; the letter **b** to back up a page; the letter **q** to quit).

Enter **q** to exit the editor.

The program `ingest.sh` downloads a dataset of earthquakes in the past 7 days
from the US Geological Survey. Notice where the file is downloaded to (disk or
Cloud Storage.)

Enter the following command to run the `ingest` code:


Click *Check my progress* to verify the objective. 

## Transform the data

You will use a Python program to transform the raw data into a map of earthquake
activity:

The transformation code is explained in detail in [this
notebook](https://github.com/GoogleCloudPlatform/datalab-samples/blob/master/basemap/earthquakes.ipynb).

Feel free to read the narrative to understand what the transformation code does.
The notebook itself was written in Datalab, a Google Cloud product that you will
use later in this set of labs.

Still in the Compute Engine instance, enter the following command to install the
necessary Python packages on the Compute Engine instance:


Enter the following command to  run the transformation code:


You will notice a new image file `earthquakes.png` in your current directory if
you enter the following command:




Click *Check my progress* to verify the objective. 

## Create a Cloud Storage bucket

Return to the Cloud Console for this step. From the **Navigation menu** select
**Storage**:



Click on **Create Bucket**, then create your bucket with the following
characteristics:

* Choose a globally unique bucket name (but not a name you'd like to use for your
own projects), then click **Continue**.
* You can leave it as **Multi-region**, or improve speed and reduce costs by
making it **Regional** (choose the same region as your Compute Engine instance).

Then, click **Create**.

Take note of your bucket name. You will insert its name whenever the
instructions ask for `<YOUR-BUCKET>.`

## Store data

You will now learn how to store the original and transformed data in Cloud
Storage.

In the SSH window of the Compute Engine instance, run the following, replace
`<YOUR-BUCKET>` with the bucket name you created earlier:


This command copies the files to your bucket in Cloud Storage.

Return to the Cloud Console. From the **Navigation menu**, select **Storage**.
Click on your bucket, now click on the `/earthquakes` folder.

You should now see the following three files in the earthquakes folder:



Click *Check my progress* to verify the objective. 

## Publish Cloud Storage files to web

You will now publish the files in your bucket to the web.

To create a publicly accessible URL for the files, click the drop-down menu
(three vertical dots) on the far right of the `earthquakes.htm` file.

Select **Edit permissions** from the drop-down menu.

In the overlay that appears, click the **+ Add Entry** button.

Add a permission for all users by entering in the following:

* Select **Public** for the Entity.
* Enter **allUsers** for the Name.
* Select **Reader** for the Access.
* Then click **Save**.



Repeat the above steps for `earthquakes.png`.

Click on the name of a file and notice the Authenticated URL of the published
Cloud Storage file and how it relates to your bucket name and content. It should
resemble the following:


If you click on the `earthquakes.png` image file and then on the Public URL, a
new tab will be opened with the following image loaded:



Go ahead and close the SSH window.

## Congratulations!

You have completed this lab and learned how to spin up a compute engine
instance, access it remotely, then manually create a pipeline to retrieve,
process and publish the data.

### Next Steps/Learn More

Here are some follow-up steps:

* Check out  [USGS.gov](https://earthquake.usgs.gov/data) for complete
information. For example:  

* the latest
[20](https://earthquake.usgs.gov/earthquakes/map/#{"feed":"1491579806344","sort":"largest","mapposition":[[-85,0],[85,360]],"viewModes":{"help":false,"list":true,"map":true,"settings":false},"autoUpdate":false,"search":{"id":"1491579806344","name":"Search
Results","isSearch":true,"params":{"starttime":"1900-01-01
00:00:00","endtime":"2017-04-07
23:59:59","minmagnitude":8,"orderby":"magnitude","limit":20}}}) large
earthquakes in the world
* geodetic data
* hazard assessment data and models, and more.
* [Sign up for ](https://earthquake.usgs.gov/ens/)automatic notifications of
earthquakes in your area.

©2020 Google LLC All rights reserved. Google and the Google logo are trademarks
of Google LLC. All other company and product names may be trademarks of the
respective companies with which they are associated.

# Welcome to Your First Lab!
