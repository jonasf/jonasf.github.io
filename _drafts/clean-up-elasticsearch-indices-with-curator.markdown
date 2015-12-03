---
layout: post
title:  "Clean up Elasticsearch indices with Curator"
metadescription: "Curator is an excellent tool to automatically clean up old indices in Elasticsearch"
date:   2015-12-04 12:01:01
tags: automation elasticsearch
---

At Tradera we needed to collect more granular data about our users than we could get from Google analytics in order to try to understand the behaviour, needs and painpoints of our people visiting our site. 
To achieve this we started to publish events when users completed certain actions on our site like searching for products, placing bids or other actions that could be considered a conversion. We would then publish these events to a message queue and feed them into a Elasticsearch cluster.

**Add image of setup**

Initially everything worked really great. We had lots of new data to crunch which quite quickly helped us gain a better understanding of our users.

**image from Kibana**

After a few weeks we started running into problems. Since this was an experiment we only had a limited number of machines to run our setup on. We had run out of disk space.

Managing the disk space manually was not an option so we started looking for a tool to help us manage cleaning up old Elasticsearch indices. The tool we found was [Curator](https://github.com/elastic/curator).

#Curator installation

     pip install elasticsearch-curator

#Curator examples
#Our Curator setup