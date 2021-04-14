---
id: 0022
title: Tink Server Improvements
status: prediscussion
authors: Nicole Hubbard <nhubbard@equinix.com>
---

## Summary

Running Tink Server in production needs some improvement around reliability and telemetry.

This doc proposes the addition of OpenTelemetry data to provide traces, exposing metrics, as well as supporting a database backend that is highly available. Cockroachdb through it's postgres interface seems like a natural fit with minimal changed to the application.

## Goals and not Goals

### Goals

Update tink server to add support for:

- Using a distributed backend datastore
- OpenTelemetry Data
- Provisioning Metrics
- Extensible Data Model

### Not Goals

Changing the API from REST to GRPC

## Content

This feature will make the life of operators a bit easier because of the following points:

- Operators will have an option to use a database backend that supports high availability and can gracefully handle a single instance failing with little to no impact to the application.
- Operators will have the ability to send OpenTelemetry traces to a compatible collector of their choice.
- Operators can access metrics with details on the number of successful and unsuccessful workflows and other important metrics.
- Developers can extend the data model to store data about the hardware managed by Tinkerbell.
