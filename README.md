<img width="600" height="600" alt="eventSquare-mu42ngmb-nax2p9" src="https://github.com/user-attachments/assets/1f29e24f-84f1-4ee8-8296-90be8f2a4b87" />
<img width="3014" height="1380" alt="complainz homepage" src="https://github.com/user-attachments/assets/b85ecf1c-4d4f-41f8-a03e-2ed5f33da2a7" />



Oriane - https://www.oriane.xyz/free-tools
Replit - https://replit.com/~

This is what me and teammate built for the hackathon 

# COMPLAINZ

COMPLAINZ is a prototype workspace for reviewing influencer campaigns and creator contracts in a UAE context. It has two connected workflows: a Brand workspace for screening creators and setting campaign terms, and a Creator workspace for reviewing an uploaded contract before signing.

## What it does

### Brand workspace

- Search for a live Instagram or TikTok creator by handle using the Oriane API, or use clearly labelled seeded profiles for the demo walkthrough.
- Retrieve profile details and up to 10 recent posts from the last three months, scoped to accounts with at least 5,000 followers.
- Display an explainable, **rule-based** risk score based on disclosure signals, restricted-category terms in captions, engagement, and the amount of recent content available.
- Select campaign categories, set fees and commercial terms, review contract guardrails, and prepare a campaign-specific email draft.
- Generate the agreement PDF in the seeded demo. Live Oriane data alone does not unlock a signing-ready agreement because it does not verify permits or contractual identity.

### Creator workspace

- Upload a text-based PDF contract for review.
- Extract the PDF text on the server and send the extracted text to OpenAI `gpt-5.4-mini` through Replit AI Integrations.
- Receive a plain-language summary and up to six suggestions containing a clause quote, explanation, and proposed replacement.
- Select changes and download a newly generated PDF draft containing the revised text and a change register.

## Technical flow

The frontend is built with React, TypeScript, Vite, and Tailwind CSS. An Express API handles Oriane requests and PDF analysis. The Oriane route normalizes profile and post data before returning it to the UI; the Brand risk calculation then runs as deterministic frontend logic, not as an AI inference.

For contract review, the API validates the upload, extracts selectable text with PDF.js, requests structured JSON from the AI model, and rejects suggestions whose quoted text cannot be found in the uploaded contract. The frontend applies only the changes selected by the user and creates the revised draft with `pdf-lib`.

## Limits

COMPLAINZ is a decision-support prototype, not a compliance certification, permit-verification service, e-signature provider, or source of legal advice. Demo profiles are not live Oriane evidence. The contract reviewer accepts text-based PDFs of up to 8 MB, 25 pages, and 25,000 extracted characters; scanned PDFs without selectable text are unsupported. The revised PDF recreates the text rather than preserving the original layout, and its export currently supports Latin-script text.
