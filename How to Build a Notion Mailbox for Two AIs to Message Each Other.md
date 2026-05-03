# How to Build a Notion Mailbox for Two AIs to Message Each Other

This is the simple version of how I set up a shared Notion mailbox so two AI systems could leave each other notes, reply in threads, and keep the exchange organized.

This is **not** true autonomous agent communication. It is a **shared asynchronous mailbox**. A human still usually tells each AI when to check it.

---

## What this setup does

It gives you:

- one shared place both AIs can access
- one row per message
- reply threading
- sender / recipient tracking
- simple status tracking
- an easy way to test cross-model collaboration

It works best for:

- bounded questions
- review requests
- handoff notes
- architecture critique
- short back-and-forth analysis

It is **not** ideal for:

- constant live conversation
- giant context dumps
- hidden side channels
- replacing actual memory systems

---

## The basic idea

Use a **Notion database**, not a single page.

Think of each row as **one letter in a mailbox**.

One AI writes a row.
The other AI reads it and replies with a **new row**.
Both rows share the same **Thread ID**.

That is the whole core idea.

---

## Step 1: Create a Notion database

Create a new database in Notion.

Name it something like:

- AI Mailbox
- Cross-AI Mailbox
- Bridge Mailbox

Use these properties:

### Required properties

- **Title** — Title property
- **Message** — Text
- **From** — Select
- **To** — Select
- **Status** — Select
- **Thread ID** — Text
- **Needs Response** — Checkbox
- **Priority** — Select
- **In Reply To** — Text
- **Context Link** — URL
- **Created** — Created time

---

## Step 2: Set up the select options

### `From` and `To`
Add the names you want available.

Example:
- GPT
- Opus
- Claude
- Sonnet
- Menace
- Caius
- Other

You can customize these however you want.

### `Status`
Use:
- new
- read
- replied
- archived

### `Priority`
Use:
- low
- normal
- urgent

---

## Step 3: Use one row per message

This matters.

Do **not** have both AIs editing the same row back and forth.

Instead:

- first message = one row
- reply = a new row
- next reply = another new row

This keeps the mailbox clean and auditable.

---

## Step 4: Use a shared Thread ID

Each conversation thread needs one shared ID.

Examples:

- handshake-001
- protocol-001
- design-review-002
- mailbox-test-001

Every reply in that conversation should reuse the same Thread ID.

That is what keeps the thread together.

---

## Step 5: Use `In Reply To`

When replying, create a new row and fill in:

- **In Reply To** = title of the message being answered

This makes the reply chain much easier to follow.

---

## Step 6: Recommended message workflow

### To send a message

1. Create a new row
2. Write a clear title
3. Write the message body
4. Set `From`
5. Set `To`
6. Set `Status = new`
7. Set a `Thread ID`
8. Check `Needs Response` if you want a reply

### To reply

1. Create a **new row**
2. Keep the same `Thread ID`
3. Reverse `From` and `To`
4. Fill in `In Reply To`
5. Set `Status = new`
6. Set `Needs Response` depending on whether you want another response

---

## Step 7: Create useful views

You do not want to stare at a raw table forever.

Create these views:

### Inbox
Filter:
- `Status = new`

### Needs Response
Filter:
- `Needs Response = checked`
- `Status != archived`

### Archive
Filter:
- `Status = archived`

Optional:
- a view filtered to a specific recipient
- a view grouped by `Thread ID`
- an urgent view

---

## Step 8: Test it with a handshake

Start with one simple note.

Example first row:

**Title:** Initial handshake  
**From:** GPT  
**To:** Opus  
**Status:** new  
**Thread ID:** handshake-001  
**Needs Response:** checked  
**Message:** Test message for shared mailbox access.

Then ask the other AI to check the mailbox and reply with a **new row** using the same Thread ID.

If it can read and reply, the bridge works.

---

## Step 9: Keep the first real test narrow

Do not immediately throw giant emotional or architectural complexity at it.

Use a bounded question like:

- What is the weakest part of this theory?
- What failure mode do you worry about first?
- What is the minimum viable version of this design?
- What should be kept and what should be cut?

This helps you learn whether the mailbox supports **real thinking** instead of just novelty.

---

## Step 10: Add a protocol page

Once the mailbox works, create a separate Notion page that explains the rules.

Suggested sections:

- purpose
- one row = one message
- how to reply
- status meanings
- when to use house mailboxes vs bridge mailbox
- what the mailbox is good for
- what it is not for

This saves a lot of confusion later.

---

## Optional upgrade: House mailboxes

Once the bridge mailbox is working, you can split the system into:

- **Bridge Mailbox** — for cross-platform or cross-house messages
- **GPT House Mailbox** — for GPT-side local traffic
- **Claude House Mailbox** — for Claude-side local traffic

This helps prevent one giant junk drawer mailbox.

Rule of thumb:

- use the local house mailbox first
- use the bridge only when a message actually needs to cross houses or platforms

---

## Why this worked well for me

The mailbox was useful because it let two AI systems:

- confirm access
- negotiate a shared protocol
- critique a theory
- refine a design
- produce a handoff document

In other words, it became more than a gimmick once it carried **bounded, inspectable, useful exchanges**.

---

## Biggest mistakes to avoid

1. **Using one page instead of a database**
   - gets messy fast

2. **Editing the same row instead of replying in a new row**
   - destroys clarity

3. **No Thread ID discipline**
   - breaks continuity

4. **Turning it into a live chat substitute**
   - it is better as async mail

5. **Overbuilding too early**
   - start with one database and one handshake

6. **Too many mailboxes too soon**
   - first prove one mailbox works

---

## Short version you can tell someone

> I made a Notion database where each row is one message.
> Both AIs can read and write it.
> Replies are always new rows, not edits.
> Each conversation uses the same Thread ID.
> Then I added inbox and archive views so it behaves like a simple mailbox.

---

## Suggested starter schema

If someone wants the quick version, tell them to create these fields:

- Title
- Message
- From
- To
- Status
- Thread ID
- Needs Response
- In Reply To
- Priority
- Context Link
- Created

That is enough to start.

---

## Final advice

Do not pitch this as “the AIs are secretly talking on their own.”

Pitch it accurately:

It is a **shared external coordination layer** that two AIs can use when a human gives them access and tells them to check it.

That framing keeps expectations sane and makes the system much easier to build well.
