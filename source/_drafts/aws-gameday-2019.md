---
title: AWS Gameday
tags: AWS-Gameday
---

It happened Wednesday, 14th of August 2019. I, amongst a number of my colleagues at [SEEK Limited](https://www.seek.com.au/)
took part in the event. I got a mixed feeling about it. It had invited targeted group of companies which was a bit contrary to the
expected mix of customers they have in the market. There are quite a mix of companies with diversified portfolio and wide range of service
usages starting from small startup to mid size organisation. But we were only five companies.


Here is the drill:

- Starts with morning tea and sugar rush injected in your system. Then  comes the fictitious user-story of the `netherland` (Not Holland).
In this case it was story of a Unicorn Rental company that needs all the services to be migrated to Microservice(uServ) based architecture
as it has lost all its employee just day before. So we need to migrate the services as soon as possible and provide better performance in terms of
latency, availability, reproducibility and cost. Of course security is quintessential but can be improved as long as it is not awfully sloppy.

- Each team is expected to provide a RESTful service with Service router for a bunch of microservices. They will have a list of microservices endpoint populated in a DynamoDB that includes the endpoints for three different services that other teams has published. The target is to use the best uServ for
each of the service dynamically as metrics changes all the times.

- All the team was given access separate user account to AWS resources to manage the services along with creating and modifying them. The accounts already came with pre-canned group of resources serving as a reference of some services that the teams are going to author. Here is the link for the documentation
https://s3.amazonaws.com/ee-assets-prod-us-east-1/modules/gd2018-loadgen/v2/readme.md
