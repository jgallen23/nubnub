# Nub Nub

Nub Nub is a Node.js implementation of a PubSubHubbub client and server.  At 
the core, it's meant to be web server and data store agnostic.  Specifics of
feed fetching are out of scope.

This library attempts to be compliant to the [PubSubHubbub spec][spec].

[spec]: http://pubsubhubbub.googlecode.com/svn/trunk/pubsubhubbub-core-0.3.html

## Handling a Subscribe or Unsubscribe request

See [section 6.1][6.1] of the spec.

    var nub = require('nubnub');
    var sub = nub.subscribe(POST_DATA);
    sub.callback      // some URL

## Verifying a Subscription

See [section 6.2][6.2] of the spec.

    // verify the subscription
    sub.check_verification(function(err, resp) {

    })

## Pushing data to subscribers

See [section 7.3][7.3] of the spec.

    // publish data 
    sub.publish(items, {format: "atom"}, function(err, resp) {
      
    })

[6.1]: http://pubsubhubbub.googlecode.com/svn/trunk/pubsubhubbub-core-0.3.html#rfc.section.6.1
[6.2]: http://pubsubhubbub.googlecode.com/svn/trunk/pubsubhubbub-core-0.3.html#rfc.section.6.2
[7.3]: http://pubsubhubbub.googlecode.com/svn/trunk/pubsubhubbub-core-0.3.html#rfc.section.7.3

## TODO

* Example server implementations with various backends?  (redis, mysql, nstore)
* Implementation of [Content Notification][7.1].
* Logic for scanning feeds.
* Logic for retrying failed verification or failed pushes as necessary.

[7.1]: http://pubsubhubbub.googlecode.com/svn/trunk/pubsubhubbub-core-0.3.html#rfc.section.7.1

## Development

Run this in the main directory to compile coffeescript to javascript as you go:

    coffee -wc -o lib --no-wrap src/**/*.coffee