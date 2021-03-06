+++
title = "This Week in Ruma"
date = 2016-04-17
extra.author = "Jimmy Cuadra"
+++

## From the editor

Greetings! My name is Jimmy Cuadra and I am the developer of Ruma.
This is the first post in a new series of updates about the ongoing progress of Ruma.
It roughly follows the pattern of weekly newsletters for other projects in the Rust ecosystem, such as [This Week in Rust](https://this-week-in-rust.org/), [This Week in Servo](https://blog.servo.org/), and [This Week in Redox](http://www.redox-os.org/news/).
I am doing this for a few reasons:

* To keep myself motivated to make progress on Ruma every week.
* To promote interest in Ruma, Matrix, and Rust.
* To provide interested parties in a way to keep track of the project's development.
* To provide interested parties opportunities to provide feedback and contribute.

Feedback is appreciated via GitHub issues, tweets, and comments on social media websites.

For the time being, I am not promising a post every single Sunday, since I am the project's sole contributor at this point, and I may not be available to work on it every single week.
That said, Ruma is a big priority for me and I expect missed posts to be the exception rather than the rule. Notably, there will not be an update next week, as I will be on vacation in Montreal!

## Notable changes to `ruma`

* Add support for full stack integration tests.
* Implement access tokens using [macaroons](https://crates.io/crates/macaroons/).
* Respond with appropriate errors when a guest operation is attempted.
  For now, Ruma does not support Matrix guest users.

## Matrix at large

This week I had a good discussion with some of the Matrix core team members about the status of the Matrix specification and the role it plays in relation to Synapse, the homeserver developed by the Matrix team.
Synapse is described as a reference implementation of the Matrix spec, but after several months working on developing Ruma against the spec, I think it is more appropriate to say that Synapse is an experimental project that serves as a proving ground for what will eventually end up in the Matrix spec.
In other words, Synapse could not currently be recreated from only the information contained in the spec, as it contains a great deal of behavior that is not represented accurately or at all in the spec itself.
This is not a bad thing, but having some clarity on the exact purpose Synapse fulfills will be important in thinking about how best to develop and maintain the spec.

Obviously, my perspective on Matrix is that of an implementor, and so the spec is my concern over any details of Synapse.
The fact that Matrix has an open specification is one of the most important things that sets it apart from other attempts at a next-generation chat platform—especially the various "open source Slack clones" that have sprung up in the last year or so.
As a result of our discussion on the topic, I've decided to put more work into helping the Matrix team improve the spec, even if it means going slower on the development of Ruma.
I think my perspective as a developer attempting to implement an interoperable homeserver from the spec alone will be very valuable in filling out the gaps in the spec.
I am exactly its target audience!
