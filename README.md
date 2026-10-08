# Smart-SSI: proven identity

A Chrome DAO initiative · October 5, 2026

[Version française](README.fr.md) · [Roadmap](ROADMAP.md) · [Architecture](ARCHITECTURE.md) · [Project board](https://github.com/orgs/chromedao/projects/3) · [Site](https://www.chromedao.xyz/smart-ssi)

## Summary

Smart-SSI lets anyone prove facts about their digital life, without exposing their data and without depending on a platform.

**The problem.** Our reputation, our skills and our activity are locked inside platforms that don't talk to each other. To prove anything, you either have to declare it (and nobody believes you) or show everything (and lose control). Meanwhile, fake profiles and bots make trust online more and more expensive.

**The solution.** Smart-SSI combines three building blocks:

- **Proof**: with zkTLS, users prove that a piece of data really comes from a real service (Strava, Spotify, a bank, a freelance platform), without handing over their credentials.
- **Interpretation**: an AI turns this proven data into simple, useful claims, for example "regular runner for 2 years".
- **Attestation**: these claims become attestations linked to the user's decentralized identity on Solana. Raw data never leaves their device.

**Why now.** zkTLS is now production-ready, Solana makes on-chain verification fast and cheap, and Europe is rolling out its digital identity wallet (eIDAS 2.0). Legal identity will soon have its standard. Proven reputation does not have one yet.

**The setting.** Smart-SSI is a [Chrome DAO](https://www.chromedao.xyz/initiatives) initiative, funded by daily NFT auctions on Solana. It is a public good: an open-source protocol, governed by holders, with no dedicated token. Its first uses serve the DAO itself: anti-sybil voting, Metaverse access, and selection of initiatives.

## The problem

Today, proving who you are online forces a choice between not being believed and exposing everything.

**Siloed identities.** Ten years of runs on Strava, hundreds of jobs on a freelance platform, a reputation built on a social network: all of it exists, but stays locked inside each service. None of it is portable, and all of it disappears if the account is closed or the platform changes its rules.

**Declaring is no longer enough.** A résumé, a profile, a bio: these are claims nobody can verify. With generative AI, producing a credible fake profile costs almost nothing. Online communities, DAOs and airdrop campaigns pay the price: a single actor can pass for hundreds.

**Verification costs too much privacy.** To prove an income, you send three full bank statements. To prove experience, you grant access to your account. The verifier gets far more than it needs, and the user has no control over what happens next.

**Existing answers are partial.** Self-sovereign identity (DIDs and Verifiable Credentials) provides the right framework, but assumes that a trusted issuer agrees to deliver attestations. Strava, Spotify or a bank do not. What is missing is a bridge between data that already exists and verifiable attestations.

## The solution

Smart-SSI turns data that already exists into verifiable attestations, in three layers.

### 1. Proof: the data really comes from the source

The user logs in to the service as usual. With zkTLS, a network of attestors observes the encrypted exchange without seeing its content, then the user generates a proof that the server's response contains a given piece of data. Nobody gets their credentials, and only the useful information is revealed.

### 2. Interpretation: the data becomes a useful claim

A raw data point ("312 recorded activities") tells a verifier little. An AI model turns it into a readable, dated claim: "regular runner, 3 runs a week for 2 years". The AI produces **derived facts**, never personality traits: every claim can be traced back to the proven data it rests on.

### 3. Attestation: the claim is bound to the identity

The claim is signed and recorded on Solana, attached to the user's decentralized identifier (DID). Only the claim goes on-chain, never the data. Any service can then verify it in a few milliseconds, without contacting either the user or the source.

### The user journey

1. Camille opens the app and creates her identity: a Solana wallet is generated in the background, with no recovery phrase to manage.
2. She picks "Prove my sports activity" and logs in to Strava in a secure window.
3. The proof is generated on her phone, and the AI suggests the claim "regular runner for 2 years".
4. Camille reviews it, approves it, and the attestation joins her profile.
5. Later, a trail-running club asks her for proof of experience for a demanding race: she shares the attestation in one click, and nothing else.

For the user, the cryptography is invisible. They only see badges they control, share and can remove from their profile.

## Use cases

Smart-SSI first serves the Chrome DAO itself, then opens up to any service that needs trust.

### Inside the Chrome DAO

- **Anti-sybil voting**: one verified person, one vote, however many wallets they control. Governance gains legitimacy.
- **Metaverse access**: the 3D hub already reserves a door for Ring holders. Spaces can open on proof: a studio for verified artists, a club for regular athletes.
- **Selecting initiatives**: a project lead proves their track record (jobs delivered, audience, sporting or artistic consistency) instead of simply declaring it. The DAO funds real talent.

### Beyond the DAO

| Use | What is proven | For whom |
| --- | --- | --- |
| Airdrops and campaigns | Unique person, real activity across several services | Web3 projects |
| Freelance reputation | Number of jobs, average ratings, seniority | Platforms, clients |
| Proof of income | Income above a threshold, without the exact amount | Landlords, lenders |
| Proof-gated communities | Practice of a discipline, membership of a group | Clubs, Discord, events |
| Hiring | Skills demonstrated through activity (published code, projects) | Companies |

In each case, the verifier gets exactly the answer to its question, and nothing more.

## Positioning

Smart-SSI does not try to say who you are legally, but to prove what you have done.

| Solution | What it proves | How | Difference from Smart-SSI |
| --- | --- | --- | --- |
| European wallet (eIDAS 2.0) | Legal identity, diplomas, licences | Official issuers (states, institutions) | Complementary: Smart-SSI covers what no institution attests |
| World ID | Human uniqueness | Biometric iris scan | No biometrics, and proofs far richer than "I am human" |
| Gitcoin Passport (Human Passport) | Humanity score | Aggregation of connected accounts | Smart-SSI proves the content of the activity, not just that the accounts exist |
| Reclaim Protocol | Raw Web2 data | Hosted zkTLS infrastructure | Smart-SSI runs its own open-source zkTLS layer, with no external provider, and adds interpretation and identity |

**Our angle:** to be the layer that connects data proofs (zkTLS) to an identity readable by humans and applications. W3C standards (DID, Verifiable Credentials) are followed, which keeps the door open to interoperability with the European wallet.

## Economic model and governance

Smart-SSI is a public good funded by the Chrome DAO: no dedicated token, no fundraising.

**Funding.** Every day, one Chrome is auctioned on Solana. Part of the proceeds funds the DAO's initiatives, including Smart-SSI: development, security audits, infrastructure.

**Governance.** Chrome holders vote on structural decisions:

- which data sources are supported first;
- the rules for issuing attestations (thresholds, validity period);
- the selection and expansion of the attestor network;
- the allocation of the initiative's budget.

**Revenue.** Smart-SSI is free for users. Professional verifiers (platforms, companies, Web3 projects) can pay a per-verification fee or a subscription. This revenue goes back to the DAO treasury, which funds other initiatives.

The loop is simple: auctions fund the protocol, the protocol strengthens the DAO's governance, and its revenue feeds the treasury.

## Trust model and privacy

Every Smart-SSI attestation rests on two distinct levels of trust, and we make them explicit.

| Level | What is guaranteed | Who is trusted | How that trust is reduced |
| --- | --- | --- | --- |
| Data proof | The data really comes from the stated service | The zkTLS attestors | Several independent attestors, selected by the DAO |
| Interpretation | The claim correctly follows from the data | The Smart-SSI issuer | Public model and rules, then execution in a trusted execution environment (TEE), then zkML in the long run |

**What never leaves the device:** login credentials, raw data, activity history.

**What is recorded on-chain:** the claim, its date, its source ("Strava") and the issuer's signature, in a Solana Attestation Service account that is closed if the user revokes it.

**User control.** Users choose which proofs to generate, approve every claim before it is issued, decide whom to share it with, and can revoke it at any time. A revocation does not erase the on-chain record, but makes the attestation invalid for every verifier.

**GDPR compliance.** Claims cover facts about activity, not psychological traits, which limits profiling. No sensitive data (health, opinions, religion) is interpreted. Processing relies on the user's explicit consent, step by step. Open point: reconciling the right to erasure with the immutability of the blockchain, which we address by putting no personal data in clear on-chain, to be confirmed with a lawyer.

## Roadmap and limits

Deployment follows four phases, each approved by the DAO before the next one starts. Progress is tracked on the [public board](https://github.com/orgs/chromedao/projects/3) and in [ROADMAP.md](ROADMAP.md).

1. **Phase 1, proof of concept**: DID on Solana, a first source (Strava or GitHub) proven through a zkTLS attestor run by the DAO on open-source components, first attestations issued to DAO members.
2. **Phase 2, internal uses**: anti-sybil voting and proof-gated access in the Metaverse, 5 to 10 supported sources.
3. **Phase 3, opening up**: public SDK for external verifiers, first paying partners, full security audit.
4. **Phase 4, decentralization**: multiple attestor network, interpretation in a trusted environment, interoperability work with the European wallet.

### Acknowledged limits

- **Dependence on source services**: if a site changes its interface or blocks access, the affected source must be adapted.
- **Residual trust**: until interpretation is proven cryptographically, the issuer remains a trusted third party, kept in check by transparency and governance.
- **Adoption**: an attestation is only worth something if verifiers accept it. That is why the first uses are internal to the DAO.
- **Legal framework**: the status of attestations and how they fit with the GDPR must be validated before opening up to third parties.

## Technical appendix

This appendix describes the implementation choices for phase 1; they will be revised at each phase.

### End-to-end flow

1. The client (mobile app) creates an ed25519 key pair and registers the user's DID on Solana.
2. The user starts a proof: the client opens a TLS session to the source through a zkTLS attestor.
3. The client generates the ZK proof over the response content; the attestor signs the proof.
4. The interpretation service verifies the proof, applies the model and suggests a claim.
5. The user approves; the Smart-SSI issuer signs the attestation and records it on-chain, attached to the DID.
6. A verifier reads the attestation and checks signature, status and date, without contacting anyone.

### Identity (DID)

We rely on the **did:sol** method, already used on Solana, rather than creating a proprietary method. The DID document holds the verification keys and can declare several devices.

### Attestations

Smart-SSI does not deploy its own on-chain program. Attestations use the [Solana Attestation Service](https://solana.com/news/solana-attestation-service) (SAS), the open standard for verifiable credentials on Solana:

- **Credential**: Smart-SSI's issuer identity on SAS, controlled by the DAO, with its list of authorized signers.
- **Schema**: one public, versioned schema per claim type (for example `runner.regular` v1). A schema can be paused without being deleted.
- **Attestation**: one Solana account per claim and per user, signed by the issuer, with an expiry date.

```json
{
  "credential": "<Smart-SSI credential>",
  "schema": "runner.regular v1",
  "nonce": "<user wallet, resolved from did:sol>",
  "signer": "<Smart-SSI issuer key>",
  "expiry": "2027-10-05",
  "data": {
    "since": "2024-09",
    "frequency_per_week": 3,
    "source": "strava",
    "proof_ref": "<hash of the zkTLS proof>",
    "model_version": "<hash of the model and rules>",
    "issued_at": "2026-10-05"
  }
}
```

Raw data is never stored; only the proof hash allows a later audit. The DAO's fee wallet pays for the accounts, separately from the signing key, so users need no SOL.

### Verification on Solana

- The zkTLS proof is verified off-chain by the issuer service; only its hash goes on-chain.
- A verifier reads the attestation account and checks that it exists, that it belongs to the Smart-SSI credential and the expected schema, that its signer is an authorized signer, and that it has not expired.
- Revocation closes the attestation account at the user's request: the attestation stops being valid, while its history stays in the Solana ledger.
- Because SAS is shared, Smart-SSI attestations sit next to those of other issuers (KYC, work, gaming), and a verifier can combine them.

### zkTLS layer

No external provider: Smart-SSI runs its own zkTLS layer, built on open-source components ([TLSNotary](https://tlsnotary.org)), so the protocol depends on no third-party service, uptime or pricing. Phase 1: one attestor operated by the DAO. Later phases: a network of independent attestors, selected and governed by the DAO.

### Interpretation pipeline

1. Extraction of the useful fields from the proven data.
2. Application of deterministic, public rules whenever possible (thresholds, frequencies, seniority).
3. Use of an LLM with structured output only for text sources, with a closed catalogue of possible claims.
4. Reliability measured on an annotated test set, with precision defined as:

```math
P = \frac{\text{correct predictions}}{\text{total predictions}}
```

Each version of the model and rules is identified by a hash recorded in the attestation, so every claim stays traceable.

---

This white paper is licensed under [CC BY 4.0](LICENSE): share and adapt it, crediting Chrome DAO. The prototype code lives in [chromedao/smart-ssi](https://github.com/chromedao/smart-ssi) under its own licenses. "Smart-SSI" and "Chrome DAO" are not covered: see [trademarks](https://github.com/chromedao/smart-ssi/blob/main/TRADEMARKS.md).
