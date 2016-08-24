# About Nuxeo Timeoff plugin

Nuxeo Timeoff is a holiday / timeoff request plugin. Based on a Nuxeo distribution (using workflow and automation chain features), this project demonstrates how to deploy a [Polymer](https://www.polymer-project.org) based site to handle requests and all the managers / HR validation process. This plugin is only the website, all the business process is handled inside the Studio Project.

This whole application is built as a single app page, with several [Iron and Paper Polymer Components](https://elements.polymer-project.org/) and [Nuxeo Elements](https://github.com/nuxeo/nuxeo-elements) to communicate with Nuxeo.

This project is a sample project, without Nuxeo support.

# Sub-modules organization

The project is split in several sub modules :
- `nuxeo-timeoff-web`: the Polymer web application.
- `nuxeo-timeoff-marketplace`: the Nuxeo package used to deploy the application in Nuxeo.
- `nuxeo-timeoff-ftest`: the functional tests.

# Description

## Roles

- Employee: an employee that do not manage anyone. It main goal in the application is to search and request timeoff.
- Manager: the manager can do the same as an employee and validate / reject / asking some changes to any pending request (see Prerequisites section).
- HR Manager: after the manager validation, the HR Manager must check if everything is legally good for the time-off.

## Features

- Managers / HR Managers dashboard that allow them to interact with employees requests (Validate / Reject / Ask for modification). A calendar view is available to compare the requested days with already accepted time off in the whole company.
- Managers / HR Managers are able to search for any employees holidays.
- Employees have a quick view on their pending requests, their incoming timeoffs and can refine search on them.

# Building

## Requirements

### Tools

- JDK 8 (Oracle's JDK or OpenJDK recommended)
- Apache Maven 3.1.1+
- Apache Ant 1.7.1+
- Npm 3.5.2
- Bower 1.7.2
- Open Source tools that will be downloaded by Maven when needed.

### Directory / User Group

 - A `hr_manager` group must be available containing the user that made the last HR validation.
 - The Nuxeo Package initiate a directory `EmployeeManagerMapping` that contains the Employee / Manager mapping. The `id` field is the employee username; and the `label` field is his manager username.

## Build

To build and run the tests, simply start the Maven build:

    mvn clean install

Build options:
- `-Pftest`: include `nuxeo-timeoff-ftest` module.
- `-DskipCleanCache`: skip cleaning the node and bower cache.

### Web application

To build only the `nuxeo-timeoff-web module` without using Maven or Ant:

    npm install
    bower install
    gulp default

## QA results

[![Build Status](https://qa.nuxeo.org/jenkins/buildStatus/icon?job=plugins_nuxeo-timeoff-master-master)](https://qa.nuxeo.org/jenkins/job/plugins_nuxeo-timeoff-master-master/)

## Deploying

Install [nuxeo-timeoff package](https://connect.nuxeo.com/nuxeo/site/marketplace/package/nuxeo-timeoff).

Otherwise use the Nuxeo package built in `nuxeo-timeoff-marketplace` module:

- From the web UI Admin / Update Center / Local Packages: upload then install
- From the command line: `nuxeoctl mp-install nuxeo-timeoff-marketplace-$VERSION.zip`

# Resources

## Reporting issues

- [https://jira.nuxeo.com/browse/NXP/component/12500/](https://jira.nuxeo.com/browse/NXP/component/12500/)
- [https://jira.nuxeo.com/secure/CreateIssue!default.jspa?project=NXP](https://jira.nuxeo.com/secure/CreateIssue!default.jspa?project=NXP)

# Licensing

[Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0.html)

# About Nuxeo

Nuxeo dramatically improves how content-based applications are built, managed and deployed, making customers more agile, innovative and successful. Nuxeo provides a next generation, enterprise ready platform for building traditional and cutting-edge content oriented applications. Combining a powerful application development environment with
SaaS-based tools and a modular architecture, the Nuxeo Platform and Products provide clear business value to some of the most recognizable brands including Verizon, Electronic Arts, Sharp, FICO, the U.S. Navy, and Boeing. Nuxeo is headquartered in New York and Paris.
More information is available at [www.nuxeo.com](http://www.nuxeo.com).
