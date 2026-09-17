# 2026-09-11 WG AP Suite Meeting
Meeting to be held 10:00 Eastern Daylight Time (14:00 UTC)

## Attendees

- Darius Kazemi, WG Chair
- Ryan Barrett snarfed.org
- David Roetzel
- Matthias Pfefferle
- Felix Hlatky
- Chris Harrelson
- Liam Roche
- Cathy Edwards
- a <trwnh.com> (they/them)
- Johannes Ernst j12t.org

## Agenda

1. Introductions, Code of Conduct
1. Server-to-Service Content Delivery proposal (Liam, Chris)
1. Continue AP suite group read through

## Minutes

### Server-to-Service Content Delivery proposal

https://github.com/explainers-by-googlers/activitypub-service-content-delivery

Mechanism to distribute public content more broadly/proactively. Complements relays, FASPs, services like tags.pub, etc.

[Key point seems to be:](https://github.com/explainers-by-googlers/activitypub-service-content-delivery#proposal)

> We propose to standardise delivery of server-wide public content...The ActivityPub specification for server to server delivery ([7.1 Delivery](https://w3c.github.io/activitypub/#delivery)) currently limits delivery to only specified recipients:
>
> > “If the object is just sent to the "public" collection the object is not delivered to any actors but is publicly viewable in the actor's outbox.”
>
> This should be expanded for servers to also deliver content to some other ActivityPub servers/services, at their discretion, when content is addressed to the “public” collection.

* Hopefully a relatively small change, reuses existing inbox delivery etc
* Alternatives:
    * FASPs: interactive public content services, separate API, supports flags like discoverability etc
    * relays: re-distribute public activities per server(s) via inbox delivery
    * new aggregate public collections
* Evan: guidance on inbox delivery in current spec is inconsistent
    * eg shared inbox section says you can distribute to additional shared inboxes
    * overall, reasonable!
    * relay protocols aren't ideal
    * new/specific inboxes per server for this? maybe
* Ryan: I like this! simple, clean
    * "just" word seems deliberate, could work around this by adding your followers collection
* a: use inbox forwarding instead?
    * eg add additional services' collections, address those collections, then recipient forwards -- `{"to": "Public", "followers", "/instance", "/partner-services"}` and then `/instance` forwards to the collection `/partner-services`
    * ideally should not bypass user/client addressing but it is technically possible for monolithic services etc to "inject" this collection to certain activities
    * conflation of Public vs "Publicized" is an issue here: https://github.com/w3c/activitypub/issues/399
* Johannes: trying to understand the impact
    * how many implementations need to change for this?
    * what's the impact? eg on content traveling farther than users' expectations
* Liam:
    * afaik doesn't require other servers to do anything new or different
    * should never change or replace user controls, access controls, addressing (esp non-public), etc
* Ryan: I'll echo those points - I like new functionality that doesn't require anyone to implement. Key point here that the other servers on the network don't have to do anything new to support this. As for how far your content travels, I'll also echo Liam and I think there can be some FUD or worry about inbox delivery as a control on where your content is visible on the network -- that is not what inboxes are for. Where you send an activity shouldn't necessarily affect who can see it. There are other controls and we should use those.
* Evan:
    * relay work was done by Mastodon, documented by a, Steve Bate, etc.
    * out of curiosity, would they prefer relays or FASPs instead?
* Eugen:
    * originally wanted relays so that servers could get more content
    * drawbacks though! users can inadvertently subscribe their server to relays without consent
    * FASPs are more powerful, flexible. relays are blunt, all or nothing. FASPs are limited to admins, customizable, directional, safer
* David: relays also hoped to help with missing replies, but we do that differently now
* Darius/Ryan: any thoughts/concerns with this proposal specifically?
* is this in scope for the current WG? ie class 1-3 but not higher?
* Bumblefudge: CG CfC or report?
* Darius: WG doesn't necessarily need "permission" from CG, but we've committed to surface normative changes to the CG, do CfCs, etc
* Evan: could be a normative change, could be a new doc
* a: still thinking about intersection w/addressing. do we just want to say this possible thing is possible? or...? what's the proposed spec change here?
* Darius/Liam: Liam could file an issue/PR with proposed language changes, we can discuss there
* Ryan/Darius: thinking hard about balance of CG-involved process here, and for every normative change, vs getting through all the work (ie normative changes) we have to do here
    * CG Reports are heavyweight and slow, want to impose them carefully, sparingly
* a: need to consider consent for sending/receiving these activities. need pairwise agreement?
* Bumblefudge: need client UX for this?

ACTION ITEMS:

- Liam: file an issue on https://github.com/w3c/activitypub/issues to start the discussion

### AP Suite read through

#### 5 Collections

[hilarity over which versions of which drafts we're all reading. spoiler: not the same ones]

* Evan:
    * Link to AS2 collections section?
    * revise note on reverse chron order and which field to use?
* a: lots of "note that" instead of just saying it
* Matthias, Ryan, Bumblefudge: note is useful, esp that the ordering should be stable
* a: Why reverse chron? Isn't the consistency requirement here way more important? 
    * Evan: useful for synchronization
    * Evan: also useful for clients directly reading collections when the common client use case is to show the most recent items, not just feeds but followers/following, outboxes, etc
* Matthias: skip auto-incrementing part?
    * also change or allow other ordering for some collections? implementation detail
* Ryan: this section is good! maybe change ordering MUST to SHOUlD but otherwise good
* Bumblefudge: how to reconcile with future-dated publishing?
* a: use older/newer instead of next/prev? this feels like it's part of the semantics of the pagination
* Evan: paging doesn't have to be offset-based. yes that doesn't work for reverse chron collections
    * but yes next/prev are confusing w/a reverse chron collection
* Darius: ...and scope now is expanding to include AS2!
* Matthias: in WordPress, "future" posts aren't published yet, they're kind of like drafts that get automatically published on their date
    * future posts aren't visible in outbox until they're published
* how do we provide for backfill? (LOLA instead?)
* a: encourage ordering using received or seen-at instead of published


#### 5.1 Outbox

* Darius: feels a bit vague?
* Ryan: yes re authorization, "permissions"
* Evan/Darius: ...? [something on the word "presented" in the section 5 reverse chron note]
* Evan: opportunity for an example here!
* David: what is an actor's profile?
    * a: some inconsistent language throughout -- spec uses actors/activities mainly but alos refers to posts and profiles 
    * Bumblefudge/Evan: their actor object, not the user-visible HTML page
* a: if a user submits a *GET* request without Authorization, specifically?

