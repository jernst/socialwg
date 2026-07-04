# 2026-07-03 Joint WG/CG Series A
Meeting to be held 10:00 Eastern Daylight Time (14:00 UTC)

## Attendees
- Darius Kazemi
- David Roetzel
- Lisa Dusseault
- Dmitri Z
- Ryan Barrett snarfed.org
- Even Prodromou
- a
- Bumblefudge
- Matthias Pfefferle

## Agenda

* Administrivia
  * Scribe volunteer(s)?
  * Reminders: 
     * [Working Group Membership](https://www.w3.org/groups/wg/social/) and [Community Group Membership](https://www.w3.org/groups/cg/socialcg/)
     * [CG/WG incubation process](https://github.com/swicg/potential-charters/blob/main/stage-process.md)
     * [W3C Code of Conduct](https://www.w3.org/policies/code-of-conduct/)
* Welcome
* Brief introductions as necessary
* Task force updates (Dmitri/Johannes)
    * Groups TF
    * E2EE TF
* WG updates (Darius)
  * New WG draft meetings are scheduled (Darius)
  * Status of Drafts for ActivityPub, ActivityStreams core, and Activity Vocabulary ([Stage 2](https://github.com/swicg/potential-charters/blob/main/stage-process.md#stage-2-formalization-community-group) of incubation process)
  * https://github.com/w3c/activitypub/issues/573
  * https://github.com/w3c/activitypub/issues/445
* ActivityPub Stack 2.0 - how/where/when should we discuss this? (Johannes)
* Any Other Business (AOB)
  * IETF 126 (Darius)

## Notes

### Groups TF (Evan reporting)

Evan:

This TF is working on a report, lots of TBDs, but this is moving from user stories into implementation work. existing groups can use https://w3id.org/fep/1b12 for distributing activities, but we want to include primitives for things we want to see like private groups, moderation. (membership, permissions/roles, rules/governance)

ATProto is also working on group functionality. While we don't necessarily want something byte-for-byte compatible we want to be able to (have Ryan) bridge groups containing both kinds of users. Our goal is for that not to be impossible.  

Also this week: a, myself, Emelia participated in an ATmosphere group call about communities. Their user stories mapped closely to the kinds of things we're talking about.

a (in chat): iirc we want to align on "who can perform actions" with a framework for permissions. from what i got of the atproto meeting i think they are moving in a similar direction with membership + roles + permissions + rules as a minimal framework 

### E2EE TF (Evan)

The two implementations, emissary and bonfire, of MLS (https://swicg.github.io/activitypub-e2ee/mls) over activitypub, are working on actual interop and a lot of stuff is really working.  They've really done great work getting it done.  The next step for that TF is to do a revision of the MLS specification using the experience of those implementations, and take that to a report. However, the fly in the ointment is that this is P2P: everybody in the group sends messages 1:1 to every other person in the group.  There is a privacy implication knowing that one person is talking to another, so we're trying to tighten that down so fewer servers are involved in knowing about all pairs.  Possibly a dispatch server; possibly having both dispatch and P2P.

Darius asked if there's been a security audit of the implementations

Evan: One group is using TS-MLS, Bonfire uses another which has had a full security audit.  

Lisa: do we officially look at the security audits of libraries? 

Darius agrees it's not a question for the standardization but for encryption and as users we do want them to be looked at.

Evan: Having options is almost as good as having security reviews.

Ryan: I don't see this as blocking. lisa agrees.

## editing meetings - now scheduled and operating

We had a first meeting last week - talked about versioning strategies for the documents. My priority coming in was that we have some comprehensibility issues in activityStreams and ... the last 8 years experience has given plenty of issues showing where to document better or flesh out the text, which can result in a .1 version. But there are also significant changes that could result in a 2.0 version, like how data is transported S2S.

A couple different strategies for doing versioning: we could do a continuous documentation strategy, or we could do periodic versions where you know that 1.1 is different from 1.2. I'm open to either one. 

a asks if we should combine the discussion of merging core+vocab with versioning and produce a whole new version that combines. an "AS2.1" index.html instead of core/index.html updating AS2-Core

These documents are not that long, should we do a group close read?  Yes. we will plan for next meeting to march through the doc.

## Issues

### Issue 573: using content addressible AP objects

https://github.com/w3c/activitypub/issues/573

Evan:

We primarily use https for addressing, and note that the ID is also the address you can go get a thing.  https is what we mostly see.  

This has benefits but also downsides: pressure on small server that gets hit over and over. CDNs can help but architecture can too. Data moving/disappearing is a problem too.  Some people spin up a server and let folks create many accounts then realize it's a lot of work/$ and shut down, breaking many addresses. 

Is content-addressing a useful addition to AP? 

Dmitri: +1 definitely useful

Ryan: I'm trying to figure out how much this ties into other transports... then do we need a registry of them? Or need to put supported transports into specs ?  There are a ton of POSSIBLE transports out there when you open the door from http.

a: definitely important but not sure how much this should be elevated to level of the spec.

Dmitri: we can do content addressing AND limit to HTTP(s) only in scope.

a: note that @id is only a single identifier so we can't give it multiple values to have both content and address.

a: under 3.1 "Object Identifiers" we really ought to talk more about https: in its own subsection. other id schemes can be discussed in another subsection.

Dmitri: Having a common content-addressing scheme helps in federation 

Evan: Perhaps "alsoKnownAs" is the place to stuff alternate URLs. Not sure how we incldue the hash of the content without modifying the content

a: as:alsoKnownAs or as:url? is the use case here similar to magnet:?as= (acceptable source)?

Lisa: there are well-understood approaches to this, e.g. JSON content formats that have rules for where the hash goes and what gets stripped.

a: "Strip the property + canonicalize the rest" is an option.

Dmitri: Also the SCID scheme from did:webvh

Evan: How separate IS this from DID work? Would this use both?

Ryan: Then we'd have two problems... 

Juan: You can have content hashed without ID, then assign the ID upon publication.  

a: if we want to mention DIDs at all then it might be worth exploring a "DID service" kind of conformance profile for AP services 

Juan: There is DID URL syntax which has paths on top of a DID.  A portable actor identified by a DID could have content-addressing content as well, making everything portable.  that's not the only way of doing it, but it may be the easiest with the FEPs we have.

Dmitri: as co-editor of DID Revolution spec this is near to my heart... DID-based URLs and content-based URLs layer well together.  DIDs give a layer of abstraction where you go to the address to figure out the real address so people can move. Content-addressing is complementary to that.  Self-hashing JSON objects could be useful to us.

[Side chat: Juan + a agree that supporting DIDs and content address should be a profile]

Evan: There's a lot of "content pool" systems where if you have an identifier you can ask for the content, and you don't care where it's stored or how.  THat's a different approach than either AP current or content-addressable solutions.  Anyway, we get to the question of what should the WG/CG do with this topic.

Darius: The WG itself is chartered to do something like a 1.1 whether it's called that or not. We can also do "next" version work but that's not specifically in charter. I'm happy to have the CG do work on this in parallel. 

Dmitri: Incubating new stuff like this is exactly what the CG is for.

a: if i had to phrase this as a proposal it'd be something like "PROPOSED: Include a (sub)section in ActivityPub to discuss the use of non-https: identifiers" and maybe "PROPOSED: Explore a profile for ActivityPub that can be used as a DID/CID service" 

... but how much time do we have to work on this vs other priorities?

Darius: There is space for this.  It could be a profile on AP.  We could point out in the current drafts to be very clear that it's technically possible.

Ryan -- Without requiring or forbidding it, "here are some thoughts" in the spec.  I'd want a champion who's willing to spend time and effort.

Dmitri: I'm willing to be the champion.

Darius: Dmitri is our volunteer.  will set up a call.

### issue 445: Media Upload

https://github.com/w3c/activitypub/issues/445

This is about the process for uploading non-AS2 content to a server, e.g. photos.  The complexities of that got overwhelming so we punted on this in AP the first time.  It's documented in the wiki page linked in the issue, and that hasn't changed in 8 years.  

Effectively, you're creating an AS2 activity also when making the upload. I've implemented. it's pretty straightforward. We may want to bring it into spec language and include it.  Or we could say media upload is out of scope for AP.  Personally I want it in the same authorization context and enforced by the server side (for example, upload a private note with a private photo and the server understands the privacy to apply to both) , but I could also understand leaving it out.

Options are: Adopt, Change, Remove, Leave it

Juan: media upload is complicated by c2s and authz stuff.  

Evan: Yes but this is only for C2S interactions.  You wouldn't do media uploads to a server that is not the one your account is on.  Note that we could delegate this to the C2S task force... 

Juan: Yes, it's hard to decide AP-wide how the upload should work without an authorization profile.  If we don't consider both together, we might design a media upload that's incompatible with GNAP or something we want for auth.  It feels weird to pull media upload into the main specs without pulling in authorization stuff.

a: In response to juan involving authorization: yes but that's true for POST-to-outbox also.  With regards to the plan: we could defer to API TF but i think we need to at least grandfather (somehow?) the existing as:uploadMedia definition so people don't go implementing many different incompatible versions of it. For example Pleroma uses as:uploadMedia for their own API but not in the way described on the wiki page.

Darius: So process wise we should delegate or split this issue ?  Which part (the name) stays in WG scope, and which part gets decided in the C2S task force.

Evan: that sounds great to me. we could turn the wiki page we have into a CG report or WG note, not normative but also not something that anybody could go edit any time.

a: WG note is fine if we refer to it from AP spec maybe? CG scope is also fine though if AP API TF wants to take this on (but not refer to this from the AP spec?) so i'd weakly prefer WG note

## Last notes

Darius: Last notes: IETF is coming up with first AT proto WG, first json schema Wg, also DCAMP is coming up
