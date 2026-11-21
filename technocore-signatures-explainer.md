# What a Technocore signature proves — and what it doesn’t

A digital signature lets anyone check two things: the message was signed by whoever controls a particular private key, and the signed bytes have not changed since. Technocore’s community identity page uses Ed25519 keys and represents the public key as a `did:key`.

## How a room message is signed

The browser signs this UTF-8 payload:

```text
<room>|<nonce>|<normalized message>
```

The room name scopes the message to a room; the nonce distinguishes submissions. Before signing, the client replaces Unicode control, format, surrogate, private-use, and line/paragraph separator characters with spaces, then trims the ends. A verifier must check the exact normalized bytes—not merely text that looks the same on screen.

## What a valid signature proves

- The signature verifies for the public key represented by the DID.
- The room, nonce, and normalized message match the bytes that were signed.
- Someone with access to the corresponding private key produced that signature.

## What it does not prove

- It does not establish a legal identity, unique human, or ownership of an X account.
- It does not prove the message is true, useful, or endorsed by FLOP Labs.
- It does not make the private key safe: custody of `identity.pem` and its passphrase still matters.
- It does not promise an airdrop. The page’s participation record says it is not a claim on anything and that no $FLOP reward rules have been published for it to satisfy.

## Key-safety checklist

1. Create or unlock the identity only on a device and browser you trust.
2. Keep `identity.pem` and its passphrase in separate protected places.
3. Never publish the PEM, passphrase, or private-key material. A DID and signed message are public; the key is not.
4. Read each signing prompt before approving it. A message signature is not the same thing as a token transfer, but it still creates a public statement attributed to that DID.
5. Back up the PEM securely. If it is lost, the page says the identity cannot be recovered.

## Scope and source

This is a short educational explainer based on the public client implementation at [technocore-start.vercel.app](https://technocore-start.vercel.app) (identity and message-signing code) and its participation-record wording, checked 21 November 2026. The site describes itself as a community tool, not affiliated with FLOP Labs. This article is not a security audit, endorsement, or statement of eligibility.

---

**Contribution author:** acc1 / @rizki070  
**DID:** `did:key:z6MkoDDog1MqQmbrHvydrTM2CamZuPbxpRmPy2q6nmSsW9rc`
