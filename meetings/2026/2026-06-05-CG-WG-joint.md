Meeting to be held 10:00 Eastern Daylight Time (14:00 UTC)

## Attendees

* Darius Kazemi
* Dmitri Zagidulin (I.E.)
* Lisa Dusseault
* Chris Harrelson
* Evan Prodromou <acct:evanprodromou@socialwebfoundation.org>
* David Roetzel (Mastodon)
* Ryan Barrett snarfed.org
* Philippe Le Hegaret (W3C)
* Charles Iliya Krempeaux <acct:reiver@mastodon.social>
* Juan Caballero
* 

## Proposed Agenda

* Administrivia
  * Scribe volunteer(s)? Lisa
  * Reminders: 
     * [Working Group Membership](https://www.w3.org/groups/wg/social/) and [Community Group Membership](https://www.w3.org/groups/cg/socialcg/)
     * [CG/WG incubation process](https://github.com/swicg/potential-charters/blob/main/stage-process.md)
     * [W3C Code of Conduct](https://www.w3.org/policies/code-of-conduct/)
* Welcome (Darius / Dmitri / Johannes)
* Brief introductions as necessary
* Task force updates
    * Website TF
* WG updates
  * [TPAC 2026 Dublin](https://www.w3.org/events/tpac/2026/tpac-2026/) ([session request](https://github.com/w3c/tpac2026-meetings/issues/3))
  * Adopting the SocialWG drafts: ActivityPub, ActivityStreams core, and Activity Vocabulary as WG editors' drafts. ([Stage 2](https://github.com/swicg/potential-charters/blob/main/stage-process.md#stage-2-formalization-community-group) of incubation process)
  * [Combine Activity Streams 2.0 Core and Activity Vocabulary into one document activitystreams#707](https://github.com/w3c/activitystreams/issues/707)
  * [Why isn't there an Actor type? activitystreams#755](https://github.com/w3c/activitystreams/issues/755)
* Any Other Business (AOB)

## Notes

### Update on WG meeting frequency

Darius: Currently we have joint calls on 1st/3rd weeks of the month. We're going to add calls on the 2nd/4th weeks of the month specifically for maintenance of the core docs, similar to Evan's meetings from before but as official WG calls since we've decided to adopt those.  You'll get notifications if you're in the WG.  

Evan: is it going to slow us down to go from 4 sessions working on draft issues to 2/month? 

Darius: We could make them longer as well. That can be a drag with virtual meetings but people have found them too slow.

Dmitri: Let's also make use of asynch time. Synchronous meetings are expensive for everyone.

Evan: I'll try to shift to more asynchronous. I'll probably make that a regular schedule and open call for my own self, unofficially.  

Darius: We still need to make sure who's a WG member for making substantive contributions in those calls.

### Introductions

Charles: background in math and computer science. been in tech for 30+ years. created 1st neo-bank in Canada (koho), created 1 of 2 identity verification services in Canada (trulioo), created social-media company hootsuite. formerly at electronic arts (ea). work on number of fediverse projects and services.

### Updates Task forces

Evan: Web site task force is updating activitypub.rocks lately, distributing responsibility for content. We had a working meeting Tuesday and posted news items. Check out the [repo](https://github.com/swicg/activitypub.rocks) for that; if you have ideas for content it would be great to add it.   We're going to maintain a 2-week pace for updating the site. 

Lisa: New version of LOLA portability draft is 0.3, it deals with references that would become a problem. Most notably, copied the content from the FEP that defined movedTo with the author's permission.

### TPAC Dublin (Oct)

https://www.w3.org/events/tpac/2026/tpac-2026/
https://github.com/w3c/tpac2026-meetings/issues/3

PLH: planning WG to meet 1.5 hours at TPAC

Darius: Agenda will include topics that may get feedback from other folks from other WGs. It might be a little early to figure out an exact agenda, we should do that around September.

PLH: It's a great opportunity to talk to folks in related groups like the WebAuthn, FedId, Linked Web storage groups.

Darius: We can certainly think about joint meetings and hallway conversation are also important.

Evan: A hackathon event, with a new spec to work with, would be interesting

PLH: You only asked for one slot; However note that if somebody has an idea for a new topic we also have time for breakout sessions proposed by individuals.  

### SocialWG Drafts

Evan: Version 1.0 and 2 of the docs are on their own branches. This allows us to do errata on one branch but make substantive changes on the other. WE continue with the same workflow as before: tracking issues, coming to consensus on changes, making PRs, merging them. 

Darius: I need to update the readmes but yes.

Evan: I encourage everybody to do a close read of ActivityPub Core, Streams and Vocabulary If we wait until September to do careful reviews, we will not meet our goals. Please make a goal of reading one draft by next meeting and add one issue. 

#### Combine Activity Streams 2.0 Core and Activity Vocabulary into one document

* [Combine Activity Streams 2.0 Core and Activity Vocabulary into one document activitystreams#707](https://github.com/w3c/activitystreams/issues/707)

Evan: We have 2 documents that define Activity Streams: AS/2 core and vocabulary. Core talks about JSON-LD and the base types like Object, Collection. Vocabulary has the social networking types like images, shares, checkins, invites. Base was a document from the OpenWeb foundation that we brought from there to W3C.  They were not using JSON-LD, so they had to add some structural items. Their vocabulary was a living doc and types added by members would get merged. Do we still need the separation between these new documents? combined they're 30k words.  There's repetition of the base/core stuff in both.

Personally I think they link to each other only once or twice so to know how they interact you have to kind of know already. 

Darius: As an individual I think it's a good idea; but as chair let's bring up the problems A brought up in the issue.  Vocabularies on their own are useful.  If the document is well-formatted, somebody could use the vocabulary for their software without using Streams. 

PLH: We see vocabularies in rec-track docs but also in registries. What do users need at the end? If you need to revise the vocabulary often and don't need patent commitments, put it on the registry track. The Working Group can make its own process to update those registries, including telling people can add to a vocabulary by editing a wiki.  

Evan: You can use AS/2 vocabularies outside of AS documents. E.g. the AlsoKnownAs property in VCs and DIDs.  I think a joint document does not preclude that. 

Darius: Looking into registries is good

Evan: Can we go ahead with the proposal to merge the docs?

PLH: They are two separate issues; merge the docs or not, and use a registry or not. 

Juan: Some things should be specs and NOT registries because you ask implementations to support all the vocubulary items (for each version) and implementors need time to put that all in there.  

Evan: Yes I agree core vocabulary should be in one document. Remember we have the means to do extensions in additional W3C docs or FEPs.  That "core" vocabulary, for lack of a better word, can be added to by registration without registration being able to subtract.

PLH: Requiring a basis is still consistent with having a registry. Figure out what you want to happen and we will figure out how to organize it.

Darius: Let's send to the mailing list as a formal proposal and update the issue to reflect this conversation

#### Why isn't there an Actor type

  * [Why isn't there an Actor type? activitystreams#755](https://github.com/w3c/activitystreams/issues/755)

Evan: Object, Collection, Link are defined as supertypes.  There's a whole section of supertypes of Actor: user, application and service.  But unlike Object, Collection, Link and Activity, we don't have an Actor supertype.  James Snell removed it late in the ActivityStreams work because it didn't define any properties.  Our problem is now that we still describe this supertype even though it was removed. We can make our documents more readable by explaining why there's no Actor type.

The type in ActivityPub is *ducktyped*.  It is an actor because it has an inbox and outbox and *does not need* to be an ActivityStreams Actor object.  I'm not sure it makes sense to reopen the core issue of whether we have an Actor type, but at least we should describe the confusion here. 

Charles: One thing that's been challenging especially for new people, is there's 3 big specs plus JSON-LD.  Understanding it is challenging and I get tripped up and I've been in this space for a while. A single document would be easier to understand.

Ryan: It would be straightforward to merge the AS Core and Vocab specs.  But it would not be so straightforward to also merge ActivityPub.  Our effort would probably be better spent elsewhere.

Dmitri: I see both sides of the argument; a single spec would be amazing but there *are* projects that use ActivityStreams and not ActivityPub.  ActivityPub also introduces some profiling of AS.  I wonder if, once we merge AS Core+Vocab, then ActivityPub can be more clear what it modifies from that joined document.  It's a data model profile of AS. 

Darius: +1 to what Dmitri's saying, and Juan's saying in the chat, and it would be loads of work.  Back to the original issue (though it's good to discuss what are we even doing)...

Evan: I feel like we have a wide range of remedies for the Actor confusion issue.  
* WE could just add a note about the architectural decision. 
* We could reintroduce Actor as a supertype. 
* We could rationalize AS Actors with AP Actors which goes pretty far.  
* Then the most work is merging together.

I'd at least like to make sure we don't make uses of ActivityStreams harder.

Darius: We can also have non-WG documents: explainers etc.

PROPOSAL: Merge the ActivityPub and AS2 recommendations into one document
RESULT: consensus but not unaminous AGAINST merging these two.

Evan: Adding a note is the mildest thing we could do. 

Darius: We don't even need to put that one to a vote, go ahead and write an editorial note. 

### Other discussion

Evan: Do I now start to bring issues to each of these?  Darius: Yes

Evan: note https://european.social/

