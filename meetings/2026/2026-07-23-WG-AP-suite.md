# Social WG AP Suite Call 2026-07-23

## Attendees
 - Darius Kazemi
 - a <trwnh.com>
 - plh
 - Evan Prodromou <acct:evanprodromou@socialwebfoundation.org>

## Minutes

Evan: We are going to start by going around the room and taking turns reading aloud sections of the ActivityPub spec and discuss as a group if there are things missing.

### Metadata, document header info, front matter

plh: [The doc](https://w3c.github.io/activitypub/) says 2024 and a CG report -- I'd expect it to be an editor's draft and to be dated 2026 since there were recent merges.

Evan: We also have a dead link in the test suite. We have an open ticket for it and we've been reluctant to remove the link to the test suite because we should have a test suite. I suggest that until we have something to link we should remove it. I don't know what else we do.

plh: Sounds good to me.

Evan: Anything else about the metadata in the header?

plh: I'm changing it to be an Editor's Draft, remove the dead test suite URI. Errata points to a wiki page, is that still accurate?

Evan: yes

plh: URI of the WG needs to be updated, the group is the Working Group and not the CG, do we want to keep the implementation report? We need one but there's no point if there's no test suite.

Evan: Okay let's take that out of the metadata.

plh: How about the Editors? Right now it's Christine and Amy listed.

Darius: How do we handle this for former editors?

plh: There's a former editors field.

Darius: Great, then at the moment Evan is an Editor and Christine and Amy can be former editors. Do we need more than one?

plh: I recommend more than one Editor, yes

Darius: Then we need to find additional Editors.

Evan: How about the Authors list?

Darius: This isn't a 2.0 ground-up rewrite so I think the Authors can and should all stay.

(updating Activity Streams and Activity Core references)

See https://github.com/w3c/activitypub/pull/586

### Abstract

- terms: protocol, API, decentralized, social networking, federated, client, server (definitions?)
- "based upon" (?)
- DK: room for more content; [CSS 2.1](https://www.w3.org/TR/CSS2/) and [DID 1.1](https://www.w3.org/TR/did-1.1/) have 3x-4x of the content
  - a: 43 words currently, "abstract" is usually 150 words in my experience, so yes could be 3x the length 
- What else could we include?
    - Activities?
    - RESTful (or at least HTTP)
    - Features and abilities
    - "Version 1.1 is related to 1.0 in these ways...""
- a: The word "content" -- one might assume this is activities but practically speaking it might not be
- EP: we do more than just create/update/delete. Social graph management (follow, etc.), Reactions (Like, Announce, ...)

### Section 1 - Overview

- Should this be "Introduction"?
- Two layers
- protocol, called API in Abstract
- "whatever" - strong Christine-voice, not necessarily a bad thing!
- EP: three parentheticals that are all load-bearing. Might want to un-parenthesize then. We literally just talked about client-to-server API (in Abstract), now we have a client-to-server protocol, and s2s API and s2s protocol. Can we normalize this? Is it worth rationalizing all the references to C2S, S2S throughout the document to use a single term
- a: Can we define these in reSpec?
- EP: Great idea it should be a reSpec defintion
- a: worried about using terms before they're defined but I don't see a better way
- DK: usually formal terms in an intro are linked forward to later in the document.
- EP: "or whatever" is a little flippant for a spec
- a: I have some concerns about accounts on servers and I understand that it's not necessarily meant to be comprehensive in this section, but there are non-account based actors. We use Actors and not accounts
- EP: What about "layers" - is layers the right term?
- a: Two protocols or two spec profiles, maybe
- EP: yes, layers implies to me higher and lower layers
- a: we use protocols throughout the rest of the document and I'm +0.5 on protocols
- EP: I'm more of a fan of APIs as a term
- EP: I notice there's a lot of confusion with plural and singular terms in the paragraph where `a user is represented by "actors" via the user's accounts on servers` -- I would feel more comfortable representing the concept of a user as an actor in a 1:1 relationship and if we need to get to many to many later.
- a: I think we should introduce the concept of an actor not necessarily tied to users in the abstract, and then later introduce that users and actors can be mapped in different ways
- DK: I wasn't around for this but we can see this section is similar to what was on activitypub.rocks for a long time. I think maybe the website didn't exist and this was intended to be a "user friendly" intro. But I don't think specs need to be friendly to a casual user
- "(More on ActivityStreams later)." - Links, something else.
- "record" is this the right term? "Actor"?
- "endpoints, or really, just URLs" (define "endpoints"?)
- "messages" -> "activities"
- Example:
    - @context
    - IDs are URLs
    - Understanding what we're looking at
    - It's JSON
- "vocabulary"
- extensibility could be clearer
- "social network" vs "social network site/service"
  - a: "social network of actors" vs one or more services? 
- "Activity Streams includes *many* of the common terms"
- "Plain old JSON" may be a strong claim
- DK: I think that someone implementing an ActivityPub service absolutely needs to understand JSON-LD. As one example, what if I see a namespace and have no idea what to do?
- Publisher responsibility vs. Consumer responsibility w/r/t JSON-LD
- "So okay" - casual
- "talk to" - mismatch of activity or messages
- "Hey nice"
- alt text for the "rest of world" image is not accurate (underspecified)
- EP: this is talking like it's all about messages and chat and missing other activties
- EP: "reading your social network's stream" and it's like, what does that mean? are we not defining this? do we need to be more rigorous
- EP: and I count 7 parentheticals here
- plh: We're talking about inbox and outbox, it sounds like a chat system but we're not using that. we're also making it sound like email and this isn't an email system. I think we need to adopt casual terms from social networks. I think we can assume people know what a social network is.
- EP: maybe we say feed instead of stream
- EP: we introduce POST and GET but we haven't said HTTP in that context. Probably worth mentioning before we use the method names
- a: Maybe we say something like "inbox and outbox are HTTP endpoints that behave differently to GET and POST requests"
- EP: the symmetry here is pleasant
- EP: Forcing the idea of inbox and outbox being message systems rather than activity systems
- EP: "non-activity object"
- DK: Introducing implicit create
- EP: "wrapped" implies same object, different type system
- EP: Could we use a full activity as the first example?
- DK: "message she composes": is she literally writing JSON
- DK: We don't have to justify how AP works and why
- EP: https://github.com/w3c/activitypub/issues/585 discussion
- "Looks up actor object"
- "streamlined submission from outbox to inbox" -- abstracting out the servers leaves out some important parts of the conversation
- "since it's an activity"
- "Since it has special public group addressed" ...
- GETting objects in the system
- curl examples? or HTTP examples? some kind of pseudocode indicating "GET to this URL, POST to that URL"
- EP: Nothing about the social graph (follow/unfollow/followers)
- DK: I think the second half is pretty strong and covers client, server, federation, Like, replies, public addressing
- a: could we add more to the overview? call the current overview a "user story" and expand with more in other subsections
- plh: https://www.w3.org/TR/vc-overview/

#### Section 1.1

- a: Past tense! document was already produced
- dk: "Maintained" instead of "produced"?
- plh: single paragraph with a simple point; does it need to be in its own section?
- a: we could expand on this, "relation to other work" as a section title, refer to SWP and/or some intro/primer/map, should at *least* mention AS2 and maybe/probably mention LDN as borrowing the "inbox" term from there. not necessarily micropub (why that one specifically?)
- EP/DK: is this still meaningful for 2026?
- overview: look at AS2 and AV
- plh: https://www.w3.org/TR/vc-overview/#high-level-view-of-the-specifications
