# Quartermaster - Examples

We have provided a set of examples to demonstrate how Quartermaster can be used to 1) explore interesting behavior of existing techniques 2) create novel techniques.

## Table of Contents

**[1. Timed](#Timed)**

**[2. Manual Events](#Manual-Events)**

**[3. Aggressive Timeout](#Aggressive-Timeout)**

**[4. Variable Traffic](#Variable-Traffic)**

**[5. Queue Sorting](#Queue-Sorting)**

**[6. Custom Statistics](#Custom-Statistics)**

**[7. Novel](#novel)**

## Timed

If you are jumping into Quartermaster, start with this example.

The timed example demonstrates a simple dependency that has cache before it. This might represent a call to a local database service, with a small in-memory TTL cache to help cover frequently requested keys and improve the response time.

This example shows how such a cache and dependency are represented as a `LRUCache` and a `TimedDependency` and how to configure properties on each.

## Manual Events

This example shows how to manually send events through an identical system to the Timed example (a dependency with a cache). This could prove useful as starter code to demonstrate how to replay live traffic through the system.

## Aggressive Timeout

This example shows how to evaluate the effects of using specific techniques on some system. A `TimedDependency` represents some remote dependency such as a different microservice. This dependency has an interesting property: failures have a higher latency than successes.

Since failures are slower than successes, it is possible to configure a timeout that allows for most successes to happen and ensures that we don't wait eventually what will be failures. This timeout would allow for faster retries when it is statistically like a failure will happen.

Events are sent through the system without any fault tolerant technique and through a duplicate system that contains a retry and timeout. Then, a summary is displayed of the events from both systems to evaluate how behavior changed. Finally, this example demonstrates `eventCompare(events, events2)`, which provides a simple diff between the two sets of events.

## Variable Traffic

## Queue Sorting

## Custom Statistics

## Novel
