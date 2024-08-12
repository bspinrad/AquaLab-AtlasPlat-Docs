
Hello and welcome to AquaLab's Custom RIPE Atlas API Platform. Whether you are an active contributor, curious user, or just passing by, this repo should hopefully have what you need.

**The service is currently in-use only within Northwestern and AquaLab and is not public. In the future, we hope to make the code open-source.**

The documentation has been broken down by user type. ***ONLY after reading the rest of this document:***
- If you are an end-user of the platform and want to schedule measurements on an existing instance of the service, go to the user guide.
- If you plan to maintain or contribute to the codebase, or you're just interested in the backend, go to the API Documentation.
- If you are acting as an administrator of an instance of the service, go to the admin documentation.
## Background and Purpose

This platform was born out of the need to schedule large batches of one-off network measurements (overwhelmingly pings and traceroutes) on the RIPE Atlas platform. Researchers in AquaLab often had large batches of network measurements that needed to be performed. While they had sufficient RIPE Atlas credits to do so, the per-account quotas set by the platform proved far too small to efficiently run the measurements that a particularly research inquiry warranted. RIPE limits users to 100 concurrent measurements, and imposes daily limits on total results and credit expenditure. Pings and traceroutes on RIPE generally take between 5 and 10 minutes to be marked as complete on the RIPE servers, depending on the probes selected. When research inquiries require 5-figure measurement counts, manually scheduling measurements becomes impractical and borderline infeasible, even with helpful wrappers like Cousteau and GOAT.

This platform's foremost purpose, then, is to be able to submit a "job" consisting of any number of measurements, and have those measurements "schedule themselves," as efficiently as possible.

In the process of building this functionality and working with the researchers, it became clear that additional features could be built in to reduce other headaches associated with Atlas. For example, CS 445, taught in the networking department at Northwestern, involves many students running smaller batches of measurements on RIPE. This incurs significant overhead, because students must create their own accounts, have the faculty "gift" them Atlas credits, and learn how to use Atlas's powerful but sometimes tricky API (or very, very limited UI). The platform instead allows students to use the Atlas platform without ever having to create an account, worry about having credits transferred, or learning the Atlas API. Instead, a number of API Keys (each corresponding to a RIPE account) are created in magnitude equal to the number of students who are using the platform. Students are then added to the user database and any student within the database can make measurement requests to the system, with the Atlas API interaction all abstracted away.

## A Note on Quotas and Ethics

It is likely that there are many users of RIPE Atlas out there who access multiple accounts to bypass the per-account quotas set by RIPE. This is not really kosher but RIPE is probably aware that some amount of this behavior occurs and has set the quotas accordingly. However, the automation that this platform provides creates an opportunity for one person to use an unlimited number of accounts (or as many accounts as they have emails) and not have to deal with the pain of account switching. Therefore, if you are using this software, AquaLab kindly requests that you use a number of API Keys no greater than the number of people who will be using the results of your measurements. This is of course a bit of a grey area. But, to give an example, if AquaLab is writing a paper with 5 co-authors, the platform should be used with no more than 5 API Keys. If the platform is being used for teaching in a class with 30 students, the platform should be used with no more than 30 API Keys.


