# Twitter Adapter

The Twitter adapter provides support for receiving and posting tweets on 
[Twitter](https://twitter.com/).

## Dependencies

- [Vantiq connector common](https://github.com/Vantiq/vantiq-connector-common)
- [Zapier connector](https://github.com/Vantiq/vantiq-connector-Zapier)

## Install

This adapter consists of a data component that supports importing tweets from Twitter and a 
control component that supports posting tweets in Twitter.

The Twitter adapter can be imported into a Vantiq namespace through the CLI:

    % git clone https://github.com/Vantiq/vantiq-adapter-Twitter.git
    % vantiq -s <profile> import

where `<profile>` provides the credentials for the Vantiq CLI.

## Tutorial

The following tutorial walks through a simple example of installing and using the Twitter
adapter.

1. Install the [Vantiq connector common](https://github.com/Vantiq/vantiq-connector-common).

2. Install the [Zapier connector](https://github.com/Vantiq/vantiq-connector-Zapier).

3. Install this Twitter adapter.

4. Create a new Zap to connect tweets to Vantiq

5. Create a simple rule that listens for new tweets