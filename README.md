# Twitter Adapter

The Twitter adapter provides support for receiving and posting tweets on 
[Twitter](https://twitter.com/).

## Dependencies

- [Vantiq connector common](https://github.com/Vantiq/vantiq-connector-common)
- [Zapier connector](https://github.com/Vantiq/vantiq-connector-Zapier)

## Install

To install the adapter, the dependencies must be installed.

1. If not installed already, download and install the Vantiq CLI from the Vantiq resources page from the server you are 
using:
    - [Vantiq Production](https://api.vantiq.com/downloads/vantiq.zip)
    - [Vantiq Development](https://dev.vantiq.com/downloads/vantiq.zip)

    Unzip and install the client in a directory that is available in your path.

2. If not installed already, download and install the [Vantiq connector common](https://github.com/Vantiq/vantiq-connector-common).

    ```
    % git clone https://github.com/Vantiq/vantiq-connector-common.git
    % cd vantiq-connector-common
    % vantiq -s <profile> import
    ```
    
    The [Vantiq connector common](https://github.com/Vantiq/vantiq-connector-common) provides a 
    utility script called `vantiq-import-adapter.sh` that makes it easier to perform 
    connector/adapter installations.

3. If not installed already, download and install the [Zapier connector](https://github.com/Vantiq/vantiq-connector-Zapier).

    ```
    % vantiq-import-adapter.sh https://github.com/Vantiq/vantiq-connector-Zapier -s <profile>
    ```

4. Download and install this Twitter adapter

    ```
    % vantiq-import-adapter.sh https://github.com/Vantiq/vantiq-adapter-Twitter -s <profile>
    ```

## Tutorial

### Send Twitter Tweets to Vantiq

The following walks through configuring Zapier to publish specific Twitter tweets
to Vantiq.

1. Log into [Zapier](https://zapier.com)
2. Click the `MAKE A ZAP!` button to start creating a Zap flow
3. For the Trigger step, choose the *Twitter* app
    - Use the *Search Mention* trigger
    - Connect to your Twitter Account
    - Enter the search term of interest (e.g. "iot")
    - Test it and ensure that a valid tweet is available
4. For the Action step, choose the *Vantiq* app
    - Use the *Publish Data* action
    - Connect to Vantiq using your Vantiq credentials to the appropriate system
    - On the *Set up Vantiq Data* page, define the data mapping
        - Set *Type* to `Twitter_Tweet`
        - Leave *Content Mapping Prefix* blank
        - Set *Content* to the *Twitter_Tweet mapping*
        - Leave *Topic* to "/system/connector/Zapier/inbound"
    - On the test page,
        - Before running test, in Vantiq, create and activate a *publish* subscription on the `/system/connector/Zapier/inbound` in the *Data > Subscriptions* UI.
        - You can use the *Find Records* page for the *Twitter_Tweet* type to see the newly created record.
5. Turn on your Zap to activate it

### Post Twitter Tweets from Vantiq

The following walks through configuration Zapier to listen for actions from Vantiq
requesting to post tweets.

1. Log into [Zapier](https://zapier.com)
2. Click the `MAKE A ZAP!` button to start creating a Zap flow
3. For the Trigger step, choose the *Vantiq* app 
    - Use the *Receive Message* trigger
    - Connect to your Vantiq account
    - For the *Action*, choose the *Twitter_PostTweet* Action
    - To test the step, click the *Connect & Continue* which will cause Zapier to subscribe to the action and wait for the message
        - In Vantiq, navigate to the *Twitter_PostTweet* procedures in *Develop > Procedures* and execute the procedure with some value for the body of the tweet.
        - Zapier should receive the posted tweet and use it as test data for the Zap flow.
4. For the Action step, choose the *Twitter* app
    - Choose the *Create Tweet* action
    - Connect to your Twitter account
    - On the *Set up Twitter Tweet* page,
        - Select *Body* for the *Message* field
    - Testing the action should post the tweet to your Twitter feed
5. Turn on your Zap to activate it allowing Zapier to continuously listen for posting tweets from Vantiq.

# Copyright and License

Copyright &copy; 2016 Vantiq, Inc.  Code released under the [MIT License](./LICENSE)