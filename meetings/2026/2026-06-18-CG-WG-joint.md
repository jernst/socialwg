# Social WG/CG Joint Call 2026-06-18

## Attendees
 - Darius Kazemi
 - Dmitri Z.
 - [Johannes Ernst](https://j12t.org)
 - [Ted Thibodeau Jr](https://www.linkedin.com/in/macted/) (he/him) (OpenLinkSw.com) // GitHub:[@TallTed](https://github.com/TallTed) // Mastodon:[@TallTed](https://mastodon.social/@TallTed)
 - a <trwnh.com>
 - Chris Harrelson
 - Emelia Smith
 - Evan Prodromou

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
    * Discovery TF
    * API TF
    * Geosocial TF
* WG updates (Darius)
  * New WG draft meetings are scheduled (Darius)
  * Status of Drafts for ActivityPub, ActivityStreams core, and Activity Vocabulary ([Stage 2](https://github.com/swicg/potential-charters/blob/main/stage-process.md#stage-2-formalization-community-group) of incubation process)
    - https://github.com/w3c/activitystreams/issues/707 (follow-on)
    - https://github.com/w3c/activitypub/issues/573 
    - https://github.com/w3c/activitypub/issues/445
* ActivityPub Stack 2.0 - how/where/when should we discuss this? (Johannes)
* Any Other Business (AOB)
    * Finishing the [extensions policy](https://github.com/swicg/extensions-policy)

## Minutes

### Task force updates

* Discovery TF (Evan):
  * doc was stalled for a while, but now starting TF meetings again, had one a week ago
  * goal: fully resolve issues in the discovery doc, to get it to a CG vote towards a draft report, current document: https://swicg.github.io/activitypub-html-discovery/
  * please add issues if you find any
  * Darius: short description in calendar may be confusing for people not familiar with the work
* API TF (Evan):
  * main topic of discussion in last two weeks: OAuth and how we authorize the user of the API to a client
  * What permission structure to use? scopes vs rich authorization requests (RARs)
* Geosocial TF (Evan):
  * Met last Thu
  * Current work focus: geographical microsyntax: ways to annotate geographic tags to a post
  * Use case: add geographical data to Mastodon posts

Darius: Mastodon has changed content type in 4.6 to conform with the AP spec

* Website TF (Johannes):
  * We had a meeting with a few items in the queue for the website.
  * Investigating how we can publish updates to the world using AP, without creating a lot of work

* Trust and Safety TF (Emelia)
  * Meetings are ongoing, but don't have a second lead
  * Had catch-up meeting on the 17th
  * Content labeling draft has been written up, can be reviewed
  * Have explainer: how content warnings currently work in the Fediverse, which explains current limitations on how to do this
    * https://github.com/swicg/activitypub-trust-and-safety/pull/122 
  * Expect that content labeling will be better approach than content warnings
  * Have PR open for granular policies
    * https://github.com/swicg/activitypub-trust-and-safety/pull/121 
  * Debating what exactly the output of the TF will be.
    * Originally: we planned to produce an initial report, but the initial report was never fully written. But now we have:
    * a MD doc / FEP for content labeling
    * community draft explainer for content warnings
  * Darius: thinking of writing a blog post saying we need a second lead.
  * Emelia: need somebody with T&S experience, not just AP experience
  * Emelia: GitHub Issue: https://github.com/swicg/activitypub-trust-and-safety/issues/135
  * Emelia: NLNet funding for T&S unclear at this point (has been 7months)
  * Emelia: TF needs more involvement, only three regulars

Darius: should have a discussion on mailing list / TF to discuss resources for T&S and other TFs.

Emelia will get the discussion started in CG and TF, with help from Darius.

Evan: Sovereign Tech Fund has a new program for participats in standards organizations. But: for individuals, not TFs.

### Working Group updates

Darius: E-mail went to WG members for meeting times, Series A (first week of the month), Series B (second week, WG only)

Johannes: is there a term "ActivityPub Suite"? Need one.

Darius: there are some discussions to merge ActivityStreams Core and Activity Vocabulary documents.

### Discussion of open issues

Evan: Should we merge the docs per [activitystreams/issues/707](https://github.com/w3c/activitystreams/issues/707)? Recapping history.

Chris: Didn't we decide in last meeting?

Darius: Only took the temperature of the room. 

Dmitri: +1 to merging. 707 proposes various mechanisms. 

a: Reading AS Core, there is a lot of redundancy that should be in Vocabulary.
  * proposed first step: core is about format, so move vocab stuff to Vocabulary, deduplicate Core and refocus it on the document format and the serialization stuff
  * proposed second step, if we decide to do that: merge Vocabulary back into AS stream
  * one argument for two docs: can use Vocabulary without format (e.g. as JSON-LD or Turtle); specs refer to just Vocab
  * if we want a single entry point, we should define that, and guide reader to what to read in what order -- the "activity suite" can refer to core, vocab, pub

Darius: awkward to point people to many documents. Can overlook. Fewer specs is better. Can write the document so people can pick and choose, doesn't need separate docs

Dmitri: no reason we can't have a single doc with three chapters.

Johannes: Spending too much time on issues like this. Let's spend our time on issues that matter more.

Emelia: maintenance burden: three docs are harder to maintain than one. Also developers may not find what they are looking for.

Dmitri: are there strong objections?

a: Would like to preserve the separation between vocabulary and the format. You should be free to implement one and not the other. Merging all docs would be less confusing but only for people who want to implement the whole thing.

a volunteers to create a PR to move vocabulary items from core to Vocabulary.

Darius: hear clearly that format and vocabulary need to be usable separately. But most of us want single document. Document PRs may be more exp

Johannes: I like what you presented Darius as a majority position. There's always the question of what the architecture is and what we want people to use separately and what we do not. Right now AP is difficult to implement because it's a big collection of optional features. Simplicity of specification should come ahead of generality. I also think we should simplify and reduce the amount of possible decisions to make when implementing.

Evan: creating issue to track the need of being able to use vocabulary independently. https://github.com/w3c/activitystreams/issues/784

a: have URIs assigned for the concepts defined in Core vs Vocabulary. what is the migration strategy?

Darius: task for the people who work on the document.

Emelia: have first-hand experience how developers get lost. (anecdata)


### Decision

PROPOSED: combine the Activity Streams Core and Activity Vocabulary specification documents into a single document, understanding that vocabulary should remain usable on its own.

+1 from Dmitri, Evan, TallTed, Chris, Darius, Emelia, Johannes 
-0 from a -- still concerned about the merge but not formally objecting

### Process

Emelia: Johannes created document for meeting mechanics process (announcing, note taking etc). Should we have a second document describing what task force lead responsibilities are.

Dmitri: will open an issue.
