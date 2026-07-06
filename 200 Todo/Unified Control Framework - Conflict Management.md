# UCF Control Conflict Management


## Problem Statement

When manually linking a package control to a UCF canonical control (e.g., sg-10), the system currently **saves the link immediately** without any conflict resolution. This causes issues:

1. **Blank new controls** — When Package B Control 2 is newly linked to the same UCF as Package A Control 1, Control 2 remains blank even though Control 1 already has implementation answer, owner, linked resources (policies, processes, risks), and audit guidance.
2. **No opportunity to manage conflicts** — The user never gets a chance to review what data already exists on peer controls before the link is committed.
3. **Multi-peer complexity** — When multiple peer controls exist (from several packages), each may have different linked resources. The user should be able to review and selectively adopt existing data.
   
---

## Proposed UX Flow

### Linking a UCF control (in the Edit Modal → UCF tab)

1. User searches & selects a UCF control to link → clicks a result
2. Instead of immediately saving:
   a. Frontend calls `link-ucf` with `preview=true` (new param)
   b. Backend returns existing peer data (answer, owner, audit_guidance, linked resources)
   c. If peers exist with data → show a "Resolve Conflicts" confirmation step
   d. If no peers or all peers are blank → link directly (current behavior)
3. In the Resolve Conflicts step:
   - Show existing data from the "richest" peer (the one with the most data filled)
   - For each field, show: current control value vs. existing peer value
   - User can choose to adopt/keep/merge for each field
   - User confirms → link is saved + chosen data is applied to the edit form
4. Edit form updates dynamically with the adopted data
5. User can still modify anything before clicking "Save Changes"

### Manual Verification / Testing Guide 

The following test scenario should be performed in the app after deployment:

1. **Setup**: Ensure you have at least 2 compliance packages deployed (e.g., ISO 27001 and SOC 2) with overlapping UCF mappings
2. **Populate data**: Open Edit for a control from Package A, add an implementation answer, assign an owner, link a policy and a risk, then save
3. **Test conflict flow**: Open Edit for a corresponding control from Package B (currently unlinked to UCF). Go to the UCF tab. Select the same UCF control that Package A's control is linked to
4. **Expected**: A conflict resolution modal should appear showing Package A's existing data
5. **Verify choices**: Select "Adopt" for answer and owner; keep current for linked resources. Confirm
6. **Expected**: Edit form should now show the adopted answer and owner. Linked resources should remain as-is
7. **Save**: Click Save Changes
8. **Verify sync**: Open Package A's control — it should reflect any changes that were synced

⚠️ Questions to address
- Should the conflict modal appear as a **separate modal overlay** or as an **inline step within the UCF tab**?
- For linked resources (policies, processes, risks), should the default be **union (merge)** or **replace**?
- Should the "richest peer" auto-selection be the default, or should the user always start from a blank slate?