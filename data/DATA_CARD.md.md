# Arannet starter data (synthetic)

Two files, same columns:

- `tamil_synthetic.csv`    - 388 messages, Tamil script
- `tanglish_synthetic.csv` - 388 messages, Tanglish (Tamil in English letters)

## Columns
| Column | Meaning |
|---|---|
| message_id | Unique row id (TA-0001, TL-0001) |
| message_text | The message |
| label | `scam` or `legitimate` |
| language_group | `Tamil` or `Tanglish` |
| scam_type | Kind of scam (`none` for legitimate) |
| source_type | Always `synthetic` (written by a template, not received by a real person) |
| source_reference | `claude_templates_v1` |
| variant_group_id | Messages built from the same scenario share this id (S01-S30 scam, L01-L30 legitimate). The Tamil and Tanglish versions of a scenario share the SAME id |

## Important rules
1. **Synthetic only.** Do not describe this as real-world data.
2. **Split by `variant_group_id`**, never by row. All rows with the same id must stay in the same split (train, validation, or test). Otherwise the model sees nearly the same message in training and in testing, and scores look falsely high.
3. **Scores on this data will be unrealistically high** because messages come from only 60 scenarios. Add your own real Tamil/Tanglish messages and use them as the final test set.
4. All links use the reserved `.example` domain and phone numbers are masked, so nothing points to a real site or person.
5. Tamil text was written without a native-speaker review. Read it and fix anything that sounds unnatural.

## Contents
- 30 scam scenarios (fake KYC, prize, OTP request, parcel fee, job scam, loan fee, UPI fraud, authority impersonation, and more)
- 30 legitimate scenarios, including look-alikes (real bank alerts, genuine OTPs, "do not share OTP" warnings, bill and delivery updates) and everyday personal messages
- Up to 8 variations per scenario (different bank, amount, link). Tanglish spelling is varied randomly (pannunga / panunga, udanae / udane).
