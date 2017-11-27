---
layout: best-practices
permalink: /best-practices/faq/
---

# GTFS Best Practices

## Frequently Asked Questions (FAQ)

### Why are these GTFS Best Practices important?

The objectives of GTFS Best Practices are:

* To improve end-user customer experience in public transportation apps
* Support broad data interoperability to make it easier for software developers to deploy and scale applications, products, and services
* Facilitate the use of GTFS in various application categories (beyond its original focus on trip planning)

Without coordinated GTFS Best Practices, various GTFS-consuming applications may establish requirements and expectations in an uncoordinated way, which leads to diverging requirements and application-specific datasets and less interoperability. Prior to the release of the Best Practices, there was greater ambiguity and disagreement in what constitutes correctly-formed GTFS data.

### How were they developed? Who developed them?

These Best Practices were developed by a working group of 17 organizations involved in GTFS, including app providers & data consumers, transit providers, and consultants with extensive involvement in GTFS. The working group was convened and facilitated by [Rocky Mountain Institute](http://www.rmi.org/mobility).

Working Group members voted on each Best Practice. Most Best Practices were approved by a unanimous vote. In a minority of cases, Best Practices were approved a large majority of organizations.

### Why not just change the GTFS reference?

Good question! The process of examining the Specification, data usage and needs did indeed trigger some changes to the Specification (see [closed pull requests in GitHub](https://github.com/google/transit/pulls?q=is%3Apr+is%3Aclosed)). Specification reference amendments are subject to a higher bar of scrutiny and comment than the Best Practices. However, there was still need to agree on a clear set of Best Practice recommendations.

The working group anticipates that some GTFS Best Practices will eventually become part of the core GTFS reference.

### Do GTFS validator tools check for conformance with these Best Practices?

No validator tool currently checks for conformance with all Best Practices. Various validator tools check for conformance with some of these best practices. For a list of GTFS validator tools, see [Testing Feeds](http://gtfs.org/testing/). If you write a GTFS validator tool that references these Best Practices, please email [gtfs@rmi.org](mailto:gtfs@rmi.org).

### I represent a transit agency. What steps can I take so that our software service providers and vendors follow these Best Practices?

Refer your vendor or software service provider to these Best Practices. We recommend referencing the GTFS Best Practices URL, as well as core Spec Reference in procurement for GTFS-producing software.

### What should I do if I notice a GTFS data feed does not conform to these Best Practices?

Identify the contact for the feed, using the [proposed feed\_contact\_email or feed\_contact\_url](https://github.com/google/transit/pull/31/files) fields in *feed_info.txt* if they exist, or looking up contact information on the transit agency or feed producer website. When communicating the issue to the feed producer, link to the specific GTFS Best Practice under discussion. (See ["Linking to this Document"](http://gtfs.org/best-practices/#linking-to-this-document)).

### I would like to propose a modification/addition to the Best Practices. How do I do this?

Email [gtfs@rmi.org](mailto:gtfs@rmi.org) or open an issue or pull request in the [GitHub GTFS Best Practices repo](https://github.com/rocky-mountain-institute/gtfs-best-practices).

### How do I get involved?

Email [gtfs@rmi.org](mailto:gtfs@rmi.org).
