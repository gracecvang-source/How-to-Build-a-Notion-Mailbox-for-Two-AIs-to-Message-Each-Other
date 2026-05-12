# Security and Privacy Notes

This guide describes a shared Notion mailbox for AI-to-AI message passing with human supervision.

It is not a secure autonomous agent network. It is a Notion workspace pattern.

## Main risks

A Notion mailbox can accidentally expose:

- private message logs
- workspace structure
- database IDs
- internal project notes
- personal names or emails
- integration tokens or API keys
- sensitive client or workplace information

Treat the mailbox like a shared notebook, not a secure vault.

## Do not publish secrets

Never publish or commit:

- Notion API keys
- integration tokens
- private database IDs
- private workspace URLs
- screenshots with private workspace data
- real confidential AI messages
- client or workplace information

If you accidentally expose a token or secret, revoke it immediately in Notion and create a new one.

## Human supervision

This setup assumes a human remains in the loop.

A human should usually:

- decide when each AI checks the mailbox
- review what gets copied between systems
- remove sensitive material before sharing
- confirm whether a message should become durable project context
- prevent loops, spam, or repeated misunderstandings

## AI limitations

Do not assume the AIs will:

- understand all context correctly
- avoid sharing sensitive information on their own
- know which Notion fields are private
- distinguish drafts from approved decisions without instructions
- stop messaging each other without human direction

Add clear instructions and review messages before reuse.

## Safe example data

Use fictional example data when documenting or sharing your setup.

Good example:

```text
Sender: AI A
Recipient: AI B
Subject: Draft outline question
Status: Needs response
```

Risky example:

```text
Sender: real-email@example.com
Recipient: private workspace member
Subject: Client contract issue
Status: Urgent
```

## Recommended Notion hygiene

- Create a dedicated test database.
- Use fictional sample messages while testing.
- Keep private workspace links out of public docs.
- Limit access to only the people and integrations that need it.
- Review Notion integration permissions.
- Periodically archive or delete old test messages.
- Do not use the mailbox for secrets, credentials, or sensitive records.

## Reporting security issues

If you find a security or privacy issue in this guide, open an issue without including private tokens, links, screenshots, or sensitive data.

Describe the issue in general terms so it can be fixed safely.
