# CoursePlay Editor 6

[![Build Status][travis-image]][travis]
[![Release][release-image]][releases]
[![License][license-image]][license]
[![Join the chat at https://gitter.im/CoursePlay-Editor-6/community?utm_source=share-link&utm_medium=link&utm_campaign=share-link][gitter-image]][gitter]

<img src="https://github.com/Courseplay/courseplay/blob/master/img/store.dds"
 alt="CoursePlay Editor 6 logo" title="CoursePlay Editor 6" align="right" />

CoursePlay Editor 6 is an enterprise-strength marketing and product analytics platform. It does three things:

1. Identifies your users, and tracks the way they engage with your website or application
2. Stores your users' behavioural data in a scalable "event data warehouse" you control: in Amazon S3 and (optionally) Amazon Redshift or Postgres
3. Lets you leverage the biggest range of tools to analyze that data, including big data tools (e.g. Spark) via EMR or more traditional tools e.g. Looker, Mode, Superset, Re:dash to analyze that behavioural data

**To find out more, please check out the [Snowplow website][website] and the [Snowplow wiki][wiki].**

## Snowplow technology 101

The repository structure follows the conceptual architecture of Snowplow, which consists of six loosely-coupled sub-systems connected by five standardized data protocols/formats:

![architecture][architecture-image]

To briefly explain these six sub-systems:

* **Trackers** fire Snowplow events. Currently we have 12 trackers, covering web, mobile, desktop, server and IoT
* **Collectors** receive Snowplow events from trackers. Currently we have three different event collectors, sinking events either to Amazon S3, Apache Kafka or Amazon Kinesis
* **Enrich** cleans up the raw Snowplow events, enriches them and puts them into storage. Currently we have a Hadoop-based enrichment process, and a Kinesis- or Kafka-based process
* **Storage** is where the Snowplow events live. Currently we store the Snowplow events in a flatfile structure on S3, and in the Redshift and Postgres databases
* **Data modeling** is where event-level data is joined with other data sets and aggregated into smaller data sets, and business logic is applied. This produces a clean set of tables which make it easier to perform analysis on the data. We have data models for Redshift and **[Looker][looker]**
* **Analytics** are performed on the Snowplow events or on the aggregate tables.

**For more information on the current Snowplow architecture, please see the [Technical architecture][architecture-doc]**.

## Quickstart

Assuming git and [SBT](https://www.scala-sbt.org/) installed:

```bash
$ git clone https://github.com/snowplow/snowplow.git
$ cd snowplow/3-enrich/scala-common-enrich
$ sbt test
```

## Find out more

| **[Technical Docs][techdocs]**     | **[Setup Guide][setup]**     | **[Roadmap][roadmap]**           | **[Contributing][contributing]**           |
|-------------------------------------|-------------------------------|-----------------------------------|---------------------------------------------|
| [![i1][techdocs-image]][techdocs] | [![i2][setup-image]][setup] | [![i3][roadmap-image]][roadmap] | [![i4][contributing-image]][contributing] |

## Contributing

We're committed to a loosely-coupled architecture for Snowplow and would love to get your contributions within each of the six sub-systems.

If you would like help implementing a new tracker, adding an additional enrichment or loading Snowplow events into an alternative database, check out our **[Contributing][contributing]** page on the wiki!

## Questions or need help?

Check out the **[Talk to us][talk-to-us]** page on our wiki.

## Copyright and license

Snowplow is copyright 2012-2018 Snowplow Analytics Ltd.

Licensed under the **[Apache License, Version 2.0][license]** (the "License");
you may not use this software except in compliance with the License.

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
