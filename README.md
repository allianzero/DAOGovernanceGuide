# DAOGovernanceGuide

DAO governance: proposals, voting, treasuries, and attacks. A DAO (decentralised autonomous organisation) is an organisation whose rules are encoded in smart contracts and whose decisions are made by token holders voting, rather than by a board or CEO.

> This guide is educational only, not financial or legal advice. DAOs are experimental, their legal status is unsettled in most countries, and their governance is frequently captured or dysfunctional.

## 1. What a DAO is, in plain language

A traditional organisation has managers who decide, and members who mostly obey. A DAO inverts this, in theory:

- **Rules in code:** membership, voting, treasury spending, and upgrades are defined by smart contracts.
- **Decisions by vote:** token holders propose and vote on changes, and approved proposals execute automatically (or are executed by a designated party).
- **Treasury on-chain:** the organisation's funds sit in a contract or multisig, visible to anyone, and move only according to the rules.

In practice, most DAOs are far less decentralised than their marketing suggests. Founders, early investors, and core teams often hold decisive voting power, and many "votes" ratify decisions already made elsewhere. The gap between DAO theory and DAO practice is the most important thing to understand about DAOs.

## 2. The governance lifecycle

A typical DAO decision follows these stages:

1. **Discussion:** an idea is debated off-chain, in forums, chats, or governance platforms (such as Snapshot, Discourse, or Discord).
2. **Proposal:** a formal proposal is written, with a specific action: spend X tokens, change parameter Y, upgrade contract Z. Vague proposals ("improve marketing") are a warning sign — executable proposals specify exactly what will happen.
3. **Voting:** token holders vote, usually weighted by how many governance tokens they hold. Voting may happen off-chain (gas-free, but non-binding until executed) or on-chain (binding, but costs gas).
4. **Timelock:** after approval, a waiting period (often 24–72 hours) passes before execution, giving dissenters time to exit or raise alarms.
5. **Execution:** the approved action is executed — by a contract automatically, by a multisig following the vote, or by a core team implementing it. Who executes matters enormously (see section 4).
6. **Review:** the outcome is visible on-chain. Did the executed action match the proposal? If not, that is a governance failure, whatever the vote said.

## 3. Voting systems and their trade-offs

### Token-weighted voting (one token, one vote)
The default in most DAOs. Simple, but plutocratic: whoever holds the most tokens decides. Wealth concentration becomes governance concentration.

### Quadratic voting
Voting power grows with the square root of tokens held, so many small holders collectively outweigh a few whales. Designed to reduce plutocracy, but vulnerable to Sybil attacks (one person splitting tokens across many wallets to gain extra power), unless identity verification is added — which reintroduces centralisation.

### Delegation (liquid democracy)
Token holders delegate their voting power to a representative (a "delegate") who votes on their behalf, and they can undelegate at any time. This improves participation (experts vote, apathetic holders delegate) but concentrates power in popular delegates, who can become de facto rulers.

### Reputation / non-transferable voting
Voting power earned through contributions, not bought on a market. Reduces plutocracy, but raises questions: who awards reputation, can it be revoked, and does it entrench early contributors?

### Multisig councils
A small group (for example, 5 of 9 signers) executes decisions, sometimes after a token vote, sometimes independently. Fast and practical, but it is a committee, not decentralised governance — and the DAO label can obscure that.

**No system is neutral.** Each one distributes power differently, and each one can be gamed. When evaluating a DAO, ask: who actually decides, and how hard is it for ordinary holders to change an outcome?

## 4. The treasury: where the money is, and who can move it

A DAO treasury usually holds the project's own tokens, plus stablecoins, ETH, or other assets from fundraising, fees, or grants.

Critical questions:

- **Where is it?** A smart contract governed by votes, a multisig, or a single wallet? Each has different security and decentralisation properties.
- **Who are the signers?** For a multisig, are signers known, independent, and geographically diverse? Or are they all team members?
- **What is the spending process?** Are grants and budgets proposed, voted on, and reported publicly, with milestones? Or does spending happen opaquely?
- **What is the runway?** How long can the treasury fund operations at current spending? A treasury denominated mostly in the project's own token can collapse in value exactly when the project needs it most.
- **Are there conflicts of interest?** Do proposal authors benefit personally from the proposals they write? Are delegates paid by the treasury they govern?

A treasury with no public reporting, no spending limits, and signers who are all insiders is not a DAO treasury — it is a company bank account with a blockchain label.

## 5. Governance attacks: how DAOs get captured

### Vote buying and flash loan governance
An attacker borrows a large amount of governance tokens (via a flash loan or a short-term purchase), votes through a malicious proposal in the same transaction or period, then returns or sells the tokens. The proposal — often "transfer the treasury to me" — executes before ordinary holders can react.

- **Defences:** voting delays (tokens must be held before a vote to count), timelocks, quorum requirements, and forbidding flash-loaned tokens from voting in the same block they were acquired.

### Low quorum and voter apathy
Most token holders never vote. If quorum (the minimum participation required) is low, a tiny, organised minority can pass anything. Attackers exploit apathy more often than they exploit code.

- **Defences:** meaningful quorum thresholds, delegation to active participants, and proposals that require broad support for treasury moves.

### Proposal spam and social engineering
Attackers flood governance with confusing, malicious, or misleading proposals, hoping one slips through while voters are fatigued or inattentive. Or they build a reputation through helpful proposals, then use it to pass a malicious one.

- **Defences:** proposal deposits (requiring tokens to submit a proposal, forfeited if it is spam), clear proposal standards, and active delegate review.

### Multisig capture
The multisig signers, who were supposed to merely execute votes, start deciding independently — or are bribed, coerced, or replaced. Token votes become theatre.

- **Defences:** on-chain execution (votes execute automatically, without a multisig intermediary), signer rotation, and public signer accountability.

### Legal and regulatory capture
A DAO with no legal entity may find its token holders, developers, or multisig signers personally liable for the DAO's actions, or subject to regulatory enforcement. Some DAOs adopt legal wrappers (foundations, associations) in specific jurisdictions — which adds legal protection but also centralised legal control. The trade-off is unresolved and jurisdiction-dependent.

## 6. Participation: how to be a useful DAO member

If you hold governance tokens:

1. **Read proposals fully before voting.** A title is not a proposal. Read the executable action, the amount, the recipient, and the rationale.
2. **Check conflicts of interest.** Who benefits, and did they disclose it?
3. **Delegate thoughtfully, or vote directly.** If you delegate, choose a delegate whose reasoning you can follow, and review their votes periodically. If you vote directly, vote on proposals that move treasuries or change rules — those matter most.
4. **Participate in discussion before voting.** The discussion phase is where bad proposals are usually caught. A vote is the last step, not the first.
5. **Track execution.** After a vote passes, verify on-chain that the executed action matched the proposal. If it did not, raise it publicly.
6. **Do not vote with borrowed tokens you do not understand.** Flash-loan voting and vote markets exist; participating in them without understanding the proposal's consequences is how governance attacks succeed.

## 7. Measuring decentralisation honestly

Ask these questions about any DAO, and score it yourself:

- [ ] What percentage of voting power do the top 10 holders control? (Above 50% means they decide alone.)
- [ ] How many distinct wallets actually vote, versus merely hold?
- [ ] Can a proposal pass without team or investor support? Has one ever?
- [ ] Is execution automatic from votes, or does a multisig/team implement it?
- [ ] Is the treasury controlled by vote-executed contracts, or by a multisig?
- [ ] Are proposal, vote, and execution all visible on-chain, with matching records?
- [ ] Has the DAO ever rejected a team proposal? (If never, voting may be theatre.)

A DAO that scores poorly on most of these is a DAO in name only. That does not automatically make it a bad project — many successful projects are effectively team-run — but it should not be evaluated or trusted as if it were decentralised.

## 8. Frequently asked questions

**Is a DAO a company?**
Legally, usually not — and that is a problem. Without a legal entity, liability, tax, contracts, and employment are ambiguous. Some DAOs use foundations or associations as legal wrappers; others operate in legal grey areas. This is jurisdiction-dependent and evolving.

**Do I need governance tokens to use a protocol?**
Usually no. Using a protocol (trading, lending, staking) is separate from governing it. Governance tokens are for voting, not for access — though some protocols add fee discounts or other benefits to holding them.

**Can DAO votes be bought?**
Yes, in several ways: buying tokens on the market, borrowing them, delegating them, or outright vote markets. Token-weighted voting is inherently buyable. Systems that resist vote buying (identity, reputation, time-weighted voting) add their own trade-offs.

**Are DAOs more efficient than companies?**
Rarely, for day-to-day decisions. Voting is slow, participation is low, and expertise is unevenly distributed. DAOs' advantage, when they have one, is legitimacy and censorship resistance for decisions that need broad consent — not speed.

> Educational content only. This is not financial, legal, or investment advice.
