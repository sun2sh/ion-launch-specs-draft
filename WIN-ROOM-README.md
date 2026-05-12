# ION Launch — Specs Repository

**Repository:** `ion-launch-specs`
**For:** ION Network Win Room — Jakarta, 19–22 May 2026
**Based on:** `ion-network-main` (the official ION network specification repository)

---

## What this repository is

This is the complete ION specification repository, assembled for the Win Room workshop. It contains everything a developer needs to build a network participant (BPP or BAP) on ION.

It is a direct copy of the live `ion-network-main` spec repo, with two additions:
1. **`docs/ion-context/`** — ION governance and hierarchy documents specific to the Jakarta pilot
2. **`WIN-ROOM-README.md`** — this file, orientating workshop participants

---

## Structure

```
ion-launch-specs/
  README.md                        ← original ion-network-main readme
  WIN-ROOM-README.md               ← this file
  CHANGELOG.md
  CONTRIBUTING.md
  LICENSE

  schema/
    core/
      v2/api/v2.0.0/
        beckn.yaml                 ← Beckn Protocol v2.0 base spec (30 core endpoints)
        ion.yaml                   ← ION extensions (8 additional endpoints)
        ion-endpoints.yaml         ← ION endpoint definitions
        ion-conditional-rules.yaml ← Conditional field rules
    extensions/
      core/                        ← Core packs (identity, address, payment, tax, etc.)
        address/v1/attributes.yaml
        identity/v1/attributes.yaml
        localization/v1/attributes.yaml
        participant/v1/attributes.yaml
        payment/v1/attributes.yaml
        product/v1/attributes.yaml
        raise/v1/attributes.yaml
        rating/v1/attributes.yaml
        reconcile/v1/attributes.yaml
        support/v1/attributes.yaml
        tax/v1/attributes.yaml
      trade/                       ← Trade sector packs
        commitment/v1/attributes.yaml
        consideration/v1/attributes.yaml
        contract/v1/attributes.yaml
        offer/v1/attributes.yaml
        performance/v1/attributes.yaml
        performance-states/v1/states.yaml
        provider/v1/attributes.yaml
        resource/v1/attributes.yaml    ← THE key file for B2C Retail cohort
      logistics/                   ← Logistics sector packs
        commitment/v1/attributes.yaml
        consideration/v1/attributes.yaml
        contract/v1/attributes.yaml
        offer/v1/attributes.yaml
        participant-logistics/v1/attributes.yaml
        performance/v1/attributes.yaml
        performance-states/v1/states.yaml
        provider/v1/attributes.yaml
        resource/v1/attributes.yaml    ← THE key file for Logistics cohort
        tracking/v1/attributes.yaml

  flows/
    trade/
      spines/
        B2C-SF/v1/spine.yaml       ← B2C Storefront (Group A — B2C Retail)
        B2B-PP/v1/spine.yaml       ← B2B Purchase Order (Group B — B2B Retail)
        B2B-CR/v1/spine.yaml       ← B2B Credit (Group B variant)
        B2C-SUB/v1/spine.yaml      ← Subscription (Group A — pharmacy)
      branches/
        RTO/v1/branch.yaml         ← Return to origin
        returns/v1/branch.yaml     ← Buyer-initiated returns
        updates/v1/branch.yaml     ← Mid-transaction changes
        cancellation/v1/branch.yaml
        during-transaction/v1/branch.yaml
        cross-cutting/v1/branch.yaml
    logistics/
      spines/
        LOG-PARCEL/v1/spine.yaml   ← Parcel (Group C — Logistics)
        LOG-HYPERLOCAL/v1/spine.yaml
        LOG-FREIGHT/v1/spine.yaml
        LOG-WAREHOUSE/v1/spine.yaml
        LOG-RORO/v1/spine.yaml
        LOG-XB/v1/spine.yaml
      branches/
        cod/v1/branch.yaml         ← Cash on delivery
        ekyc/v1/branch.yaml        ← KYC at delivery
        attempts/v1/branch.yaml    ← Redelivery attempts
        reverse/v1/branch.yaml     ← Reverse logistics
        cold-chain/v1/branch.yaml
        customs/v1/branch.yaml
        during-transaction/v1/branch.yaml
        exception/v1/branch.yaml
        incident/v1/branch.yaml
        rts-handoff/v1/branch.yaml
        value-added/v1/branch.yaml
        weight-dispute/v1/branch.yaml

  errors/
    catalog.yaml                   ← ION-8xxx errors (catalogue publishing)
    fulfillment.yaml               ← ION-1xxx errors (delivery/fulfilment)
    transaction.yaml               ← ION-2xxx errors (transaction flow)
    post-order.yaml                ← ION-3xxx errors (post-order)
    settlement.yaml                ← ION-4xxx errors (settlement/reconcile)
    logistics.yaml                 ← Logistics-specific errors
    schema.yaml                    ← Schema validation errors
    network.yaml                   ← Network/routing errors
    system.yaml                    ← System errors
    transport.yaml                 ← Transport errors
    registry.json                  ← Machine-readable error registry

  policies/
    return/v1/                     ← Return policy IRIs
    cancellation/v1/               ← Cancellation policy IRIs
    warranty/v1/                   ← Warranty policy IRIs
    payment-terms/v1/              ← Payment terms IRIs
    penalty/v1/                    ← Penalty policy IRIs
    dispute/v1/                    ← Dispute resolution IRIs
    grievance-sla/v1/              ← Grievance SLA IRIs
    registry.json                  ← Machine-readable policy registry

  docs/
    ION_Start_Here.md              ← Start here for new developers
    ION_Developer_Orientation.md
    ION_First_Transaction.md       ← Step-by-step first transaction guide
    ION_First_Transaction_Food.md  ← Food delivery variant
    ION_Layer_Model.md             ← Three-plane model explanation
    ION_Schema_Style_Guide.md
    ION_Sector_A_Trade.md
    ION_Sector_B_Logistics.md
    ION_Beckn_Conformance.md
    ION_Onboarding_and_Auth.md
    ION_Glossary.md
    ion-context/                   ← Jakarta Win Room context docs
      ION-Complete-Spec-Reference.md
      ION-ENTITY-HIERARCHY-MODEL-v2.md
      ION-Resource-Categories.md
      bu-sari-wizard.md
      bu-sari-complete-journey.md
      ION_Atlas_Developer_Orientation.md

  .github/
    ISSUE_TEMPLATE/
      field_proposal.md            ← Propose a new field
      error_proposal.md            ← Propose a new error code
      spec_issue.md                ← Flag a spec issue
```

---

## Which files to read — by cohort

### Group A — B2C Retail (ion:trade / Storefront)

| Priority | File | What it tells you |
|---|---|---|
| 1 | `docs/ION_Start_Here.md` | How the repo is organised |
| 2 | `docs/ION_First_Transaction.md` | Step-by-step first storefront transaction |
| 3 | `flows/trade/spines/B2C-SF/v1/spine.yaml` | The complete storefront API sequence |
| 4 | `schema/extensions/trade/resource/v1/attributes.yaml` | Every field in the resource payload |
| 5 | `schema/extensions/trade/offer/v1/attributes.yaml` | Every field in the offer payload |
| 6 | `schema/extensions/trade/performance/v1/attributes.yaml` | Every field in on_status |
| 7 | `flows/trade/branches/` | RTO, returns, mid-transaction changes |
| 8 | `docs/ion-context/bu-sari-wizard.md` | Non-technical walkthrough of the whole journey |
| 9 | `docs/ion-context/bu-sari-complete-journey.md` | Full JSON payloads for every step |

### Group B — B2B Retail (ion:trade / Business Procurement)

| Priority | File | What it tells you |
|---|---|---|
| 1 | `flows/trade/spines/B2B-PP/v1/spine.yaml` | B2B purchase order sequence |
| 2 | `flows/trade/spines/B2B-CR/v1/spine.yaml` | Credit terms variant |
| 3 | `schema/extensions/trade/commitment/v1/attributes.yaml` | B2B commitment fields |
| 4 | `schema/extensions/trade/offer/v1/attributes.yaml` | MOQ, bulk pricing fields |
| 5 | `docs/ION_Sector_A_Trade.md` | Trade sector full reference |

### Group C — Logistics (ion:logistics / Parcel)

| Priority | File | What it tells you |
|---|---|---|
| 1 | `docs/ION_First_Transaction_Food.md` | Logistics embedded in trade (embedded LSP flow) |
| 2 | `flows/logistics/spines/LOG-PARCEL/v1/spine.yaml` | Parcel API sequence |
| 3 | `schema/extensions/logistics/resource/v1/attributes.yaml` | Shipment resource fields |
| 4 | `schema/extensions/logistics/performance/v1/attributes.yaml` | Tracking status fields |
| 5 | `flows/logistics/branches/cod/v1/branch.yaml` | COD branch |
| 6 | `flows/logistics/branches/ekyc/v1/branch.yaml` | KYC at delivery branch |
| 7 | `flows/logistics/branches/attempts/v1/branch.yaml` | Redelivery attempts branch |
| 8 | `docs/ION_Sector_B_Logistics.md` | Logistics sector full reference |

### Group D — MSME Credit (ion:finance / Loan Application)

| Priority | File | What it tells you |
|---|---|---|
| 1 | `docs/ion-context/ION-ENTITY-HIERARCHY-MODEL-v2.md` | Finance sector in the hierarchy |
| 2 | `docs/ion-context/ION-Complete-Spec-Reference.md` | Finance CRCs and patterns |
| 3 | `docs/ION_Schema_Style_Guide.md` | How to write new schema packs |
| 4 | `schema/extensions/trade/resource/v1/attributes.yaml` | Use as template for FNC-lending pack |
| 5 | `errors/catalog.yaml` | Error codes for catalogue publishing |
| Note | Finance spine and schema packs are stubs | Group D will author them during Day 2 workshop |

---

## The spine/branch model

ION flows use two types of YAML:

**Spine** — the complete happy-path transaction from discovery through settlement. One spine per pattern (e.g. B2C-SF = B2C Storefront, LOG-PARCEL = Parcel delivery).

**Branch** — a named modification of a spine that handles a specific scenario (e.g. COD, KYC at delivery, returns). Branches are composable — a single transaction can activate multiple branches simultaneously.

The ION DevLabs Platform reads these files to render:
- Protocol Explorer swimlane diagrams (from spine.yaml)
- Variant selector and diff overlays (from branch.yaml)
- Step inspector required fields (from both)

---

## ION extension endpoints (in addition to Beckn's 30)

Defined in `schema/core/v2/api/v2.0.0/ion-endpoints.yaml`:

| Endpoint | Direction | Purpose |
|---|---|---|
| `POST /raise` | NP → ION | Submit platform dispute to ION governance |
| `POST /on_raise` | ION → NP | Returns ticket ID and SLA |
| `POST /raise_status` | NP → ION | Poll open ticket status |
| `POST /on_raise_status` | ION → NP | Returns ticket state |
| `POST /raise_details` | NP → ION | Request full ticket thread |
| `POST /on_raise_details` | ION → NP | Returns complete audit record |
| `POST /reconcile` | BAP → BPP | Initiate financial settlement after delivery |
| `POST /on_reconcile` | BPP → BAP | Returns AGREED or DISPUTED |

---

## Raising issues

Use the GitHub issue templates in `.github/ISSUE_TEMPLATE/`:
- `field_proposal.md` — propose a new field in a schema pack
- `error_proposal.md` — propose a new error code
- `spec_issue.md` — flag something incorrect or unclear in the spec

---

*Repository assembled for the ION Win Room, Jakarta 19–22 May 2026.*
*Base: `ion-network-main` commit `351441b` (27 April 2026).*
*Beckn Protocol v2.0.0 included as reference.*
