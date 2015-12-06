---
layout: post
title:  "Clean up Elasticsearch indices with Curator"
metadescription: "Curator is an excellent tool to automatically clean up old indices in Elasticsearch"
date:   2015-12-04 12:01:01
tags: automation elasticsearch
---

At Tradera we needed to collect more granular data about our users than we could get from Google analytics in order to try to understand the behaviour, needs and painpoints of visitors to our site. 
To achieve this we started to publish events when users completed certain actions on our site like searching for products, placing bids and any action that could be considered a conversion. We would then publish these events to a message queue and feed them into a Elasticsearch cluster.

**Add image of setup**

Initially everything worked really great. We had lots of new data to crunch which quite quickly helped us gain a better understanding of our users.

**image from Kibana**

After a few weeks we started running into problems. Since this was an experiment we only had a limited number of machines to run our setup on. We had run out of disk space.

Managing the disk space manually was not an option so we started looking for a tool to help us manage cleaning up old Elasticsearch indices. The tool we found was [Curator](https://github.com/elastic/curator).
Curator is a command line tool that allows you to perform several different operations on elasticsearch indices.

###Curator installation

Curator is a Python package, you can install it using [Pip](https://pypi.python.org/pypi/pip)

     pip install elasticsearch-curator

###Curator examples

We needed to delete indices older than a certain number of days and all our indices names had the following pattern myindexname-yyyy-mm-dd, for example myindexname-2015-12-01.

Our curator command to delete older indices turned out something like this:

     curator --host elasticsearch.my-domain.com  delete indices --prefix myindexname-  --older-than 4 --time-unit days --timestring '%Y.%m.%d’

###Our Curator setup

We set up a Cron job to run the Curator commands every morning.

One small gotcha was that % is a special character in the Cron tab, so at first our jobs didn't work. Escaping the timestring parameter made everything work as intended:

    --timestring '\%Y.\%m.\%d’

###Conclusion

Curator helped us solve our problem with disk space.

The data collection experiment turned out to be a success so we received additional funding to beef up our cluster, including more disk space.