# PTW Learning & Competency LMS v0.1

A lightweight, invigilated Permit-to-Work learning and assessment system using:

- Public GitHub Pages for the interface only
- Google Apps Script for authentication, authorization and business logic
- Google Sheets for controlled records
- Google Drive for practical-assessment PDFs

## Security boundary

The GitHub repository is public. Do not commit controlled procedures, learner data, answer keys used in production, tokens, passwords, private Drive links or Apps Script secrets. The included question bank is a starter and must be replaced/expanded in the controlled backend before production.

## Deployment

1. Create a new Google Sheet owned by the designated system account.
2. Open Extensions > Apps Script.
3. Add `Code.gs` and replace the manifest with `appsscript.json`.
4. Run `setupLms()` once and authorize the script.
5. Run `createFirstAdmin()` and correct the administrator email in `LMS_USERS` if necessary.
6. Deploy as a Web App, executing as the owner. Select the access option approved by your organization.
7. Copy the `/exec` URL into `API_URL` in `index.html`.
8. Commit only the frontend files to GitHub and enable GitHub Pages.
9. Activate the admin account from the public login page.
10. Add invigilators and participants, then run `createTrainingSession('invigilatorUsername',['user1','user2'])` from Apps Script for the pilot.

## Production hardening required

This pilot demonstrates the workflow. Before live HSSE use, complete a security and privacy review, replace the iterative SHA-256 password routine with a reviewed authentication provider or approved server-side password-hashing service, add server-side rate limiting, configure retention and backup, add invigilator practical scoring, add PDF finalization after sign-off, and test all authorization paths.

## Competency model

Completion is not attendance alone. Recommended evidence:

1. All learning modules completed.
2. Knowledge assessment at or above 80%.
3. Practical PTW prepared for a simple activity.
4. Invigilator observes scope definition, hazard/control selection, supporting-document selection, Toolbox Talk and handback understanding.
5. Final PDF saved in controlled Drive storage.
6. Competency validity and refresher period assigned by the document owner.

## Voice-over

The frontend includes browser text-to-speech for English, Bahasa Indonesia and Bahasa Melayu. For consistent pronunciation and offline reliability, replace this with approved recorded MP3 narration per module and language. Store audio in controlled hosting and return time-limited/authorized links from the backend.
