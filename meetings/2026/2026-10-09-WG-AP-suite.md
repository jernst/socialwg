# Social WG AP Suite Call 2026-10-09

## Attendees
 - Darius Kazemi, Chair
 - Ryan Barrett snarfed.org
 - David Roetzel
 - Chris Harrelson
 - Liam Roche
 - a <trwnh.com>
 - Evan Prodromou
 - Matthias Pfefferle

Meeting to be held 10:00 Eastern Daylight Time (14:00 UTC)

## Agenda

1. Introductions, Code of Conduct, WG Membership
2. Discuss these two related PRs
   * Clarify delivery to additional inboxes for public activities https://github.com/w3c/activitypub/pull/621
   * shared inbox delivery: servers MAY deliver to "all known" => "additional" shared inboxes 
   
3. Internationalised handles work
4. Continue AP suite group read through

## Minutes

### PRs for delivering to additional inboxes, #621 & #626

They've been out for 2-3w, we've discussed them on calls and on the mailing list, we've reached consensus. Ready to merge!

Darius: PROPOSED: Merge PRs 621 and 626 on the activitypub repo 
Five +1s, no other votes
RESOLVED: Merge PRs 621 and 626 on the activitypub repo 

### Internationalised handles

Evan: complicated because we have two user identifiers used in the wild,  HTTP URI AP ids and WebFinger handles

https://www.w3.org/community/reports/socialcg/CG-FINAL-apwf-20240608/#usernames says:
> Implementers SHOULD support remote usernames containing valid characters per [RFC7565]. For short-term compatibility, implementers SHOULD NOT use characters other than alphanumeric (A-Z, a-z, 0-9) and underscores (_).

New support tracker for handling i18n WebFinger handles! From the CG. https://swicg.github.io/activitypub-webfinger/internationalized

https://w3c.github.io/activitypub/#actor-objects has an example actor with non-ASCII characters in some fields, eg name and summary, but not preferredUsername

- Evan: wants to add more examples, including non-ASCII preferredUsername
- Darius: agreed! could also have related values with percent-encoded translations, IDNA translations for domains, etc
- Evan: ia8n mostly punted to AS2: https://w3c.github.io/activitypub/#i18n-concerns
- Eugen Rochko from Mastodon has been a vocal supporter
- Important! Difficult, lots of concerns, eg RTL rendering (esp alongside LTR), we won't specify everything, but still important to help with
- Darius: lots more opportunity for the CG here

- Evan: Ryan, how does this work in AT?
- Ryan: ASCII -ish because things are tied to domain names, but really punycode encoding

### ActivityPub spec read-through

#### 6.2 Create Activity

on activities vs objects as content

- EP: Uniformity of "all interactions are activities" is relatively clear and talking about activities being "wrappers" or "wrapping" objects makes it harder to understand
- Darius: existing language seems fine to me. In practice I usually go straight to implementing objects before implementing activities...
- a: Activities are the primary unit of content in a certain worldview, as opposed to focusing on CRUD operations on Note/Article/etc. Arrive, Listen, etc are the content in themselves

on injecting properties of the object

- Chris: should the two SHOULDs be MUSTs?
- Evan: can we think of counterexamples?
- a: could be sending on behalf of someone else; distinction between "create this object" (procedure) vs "this object was created" (notification)
- Darius: eg with quote posts?
- Ryan: yes but in S2S. harder to imagine in S2S
- Darius: see https://github.com/w3c/activitypub/issues/467, eg with Flag
- Evan: how about objects that already have ids?
  in 3.1: "However, for client to server communication, a server receiving an object posted to the outbox with no specified id SHOULD allocate an object ID and attach it to the posted object." 
- Evan: maybe change them to MUST?
- Ryan: ok but then we need to specify what happens when eg actor and attributedTo are mismatched. error?

tangent on attributedTo vs author

- a: explicit authorship (eg author field) would be more useful than attributedTo. right now attributedTo is loosely defined to include notions of ownership/controllership (e.g. this actor is authorized to modify the object) and causality (e.g. this object is attributedTo a Create activity, because the Create activity is why the object exists)
- Evan: discuss attributedTo in 3.1?
- Ryan: AS1 has "author", so "attributedTo" seems like a regression in how loosely it's defined?
- Evan: AS2 tried to generalize from social networking to broader uses. part of that
- Darius: is the word "created" defined somewhere? if not, is that ok? maybe overthinking?

on "is created"

- Darius: What does "is created" mean?
- Evan: Created objects MUST meet Section 3 requirements?
- a: so like id allocation? registering its existence somehow?
- Evan: this is also an opportunity to set `published`
- a: key part of creating I see is generating id, as discussed in section 6
- Darius: making it servable too
- a: move to explain this? not just say "is created"; explain what the server's responsibilities are


#### 6.2.1 Object creation without a Create Activity

- Ryan: link NOTE's Location header discussion to section 6's Location header discussion?
  also, in example 14, attributedTo is copied to actor, should be mentioned
- Evan: how do you know if you're getting an object or an activity? eg problem w/extension types. can work around with "multi typing" 
    - https://www.w3.org/wiki/Activity_Streams/Primer/Identifying_Activity_Objects
- Ryan: would you propose dropping this entirely?
- Evan: it was important to other editors the first time around! but maybe yes deprecate
- Darius: include rules about how server overrides properties or copies them into the Create activity? what if the client is missing information and can't generate a Create activity? note that i am more in favor of a world where clients do more and servers do less...
- Evan: a, what do you think?
- a: it's kind of a footgun -- you can try duck typing presence of "actor" or "object" to detect it is an activity but the failure case is hard to clean up -- if you send out a Create instead of the "bare activity" then your consumers will fail to understand it and that's worse than the minor convenience. it's also ambiguous when the object is or is not "transient" -- https://github.com/w3c/activitypub/issues/438 -- i'd also move to deprecate this behavior in favor of just being explicit from the start.
- Ryan: the object vs activity distinction still exists! but yes could be downplayed


#### 6.3 Update activity

- Darius: Maybe first sentence should say "when modifying" instead of "when updating", less circular definition
- EP: good time to talk about the `updated` property

#### 6.3.1 Partial updates

missing normative language?

- Ryan: lowercase SHOULD, but is it really a MUST? "should contain the entire new representation"
- Evan: We need examples here and throughout. In this case in particular it needs to be called out that it only works with the embedded node format.

```json
{
    "@context": "https://www.w3.org/ns/activitystreams",
    "type": "Update",
    "object": {
        "id": "https://social.example/note/35",
        "type": "Note",
        "content": "Hello, World! UPDATE: especially Matthias"
    }
}
```

This won't work. What do you change?!?

```json
{
    "@context": "https://www.w3.org/ns/activitystreams",
    "type": "Update",
    "object": "https://social.example/note/35"
}
```

shortcomings of the partial update mechanism

- Evan: also need a way to delete individual properties
- a: https://github.com/w3c/activitypub/issues/477
- a: Patch formats generally better and solve the problem -- Update activity can have the object be a bare id and then the patch set described in extension property.
- EP: There is a FEP, https://fediverse.codeberg.page/fep/fep/a1d1/
- Ryan patch format works but is significant new complexity. deleting properties seems like the only missing part. could we just set those properties to null instead?
- EP, Darius: Not 1.1 changes, more of a 2.0

word choice

- Chris: updating the "document" should be "object"?

error handling

- Ryan: error handling? when any of these MUSTs are violated. we don't need it everywhere, but maybe a single unified section somewhere (or one each for C2S and S2S) that says, servers return HTTP 400 on errors by default, async notwithstanding


#### 6.4 Delete activity

grammar

- Darius: missing a preposition; comma "otherwise"
- Ryan: clarify that there are 2 options? you can Tombstone or you can delete.

editorial

- EP: call out deleted datetime and formerType properties here
- Darius: back-reference Tombstone between C2S and S2S
- Ryan: some platforms' ids have content snippets, eg slugs. those can be sensitive, and deletes can preserve the id if they tombstone. worth a non-normative note on privacy/safety?

side effects for older activities, and nature of a Tombstone

- Darius: what happens to the wrapping activities? older Create/Update etc now refer to a Tombstone? not dynamically hydrating the Note referenced by the Create. is this worth warning about?
- EP: goal of Tombstone is to preserve threading and so on.
- Matthias: Can we require the 410 Gone response because some people serve a Tombstone with 200 OK
- Darius: "when an object is deleted please invalidate old references" etc?
- Matthias: too many ways to do something wrong, 404 or 410 or Tombstone or some combination. 
- EP: 404 is for repudiability, denying something ever existed. 410 can return a Tombstone
- a: Client doesn't have much control here on whether it is Tombstone or not -- should the client have an option to say "i want this gone" vs "i want this *gone* gone"? Client might bypass the server behavior by sending Update activity to change the type to Tombstone, which results in the 200 OK response Matthias was concerned about.
- David: S2S too?
- Evan: could put this in Section 3

#### 6.5 Follow activity

- EP: "when and only if" is weird grammatical construction
- EP: no pending state; where does it live before being accepted?
    - EP: https://fediverse.codeberg.page/fep/fep/4ccd/
- Ryan: behavior of transient activity without id, then later you embed the entire activity and match by shape?

NOTE: at time; next session should start over and do this section again because there's a lot left to discuss!
