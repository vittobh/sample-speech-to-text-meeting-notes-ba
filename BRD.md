# BRD — Automated Meeting Notes (Speech-to-Text Feature)

> Sanitized: client name replaced with `[Telecom Client]`.

## Project requirement overview
Brief from `[Telecom Client]` to design and develop a note-making feature for employees during video conferencing. Feature to be embedded in existing conferencing product; designed for fast iteration on existing data and feedback.

Automation via Google Cloud Speech-to-Text API.

## Competitor / open-market analysis
| Rank | API | Description |
|------|-----|-------------|
| 1 | Google Speech API | Audio → text, voice searches, voice-controlled cases |
| 2 | IBM Watson API | Audio → text, voice-controlled cases, customizable models |
| 3 | Speech-to-Text API | Speech data → text |
| 4 | Rev.AI API | Speech → text, punctuation, capitalization, timestamps, live streaming |

**Decision:** Google Speech API — best reliability + 120+ languages + selectable ML models per use case.

## Google Speech API features used
- 120+ language recognition
- Multiple ML models for accuracy
- Automatic language recognition
- Text transcription
- Proper-noun recognition
- Data privacy
- Noise cancellation (phone / video)

## Use flow
Speech during conference → BOT (backend-encoded) → Google Speech API → JSON text → post-processing & normalization → stored in DB → retrieved for automated email.

## Project details
| Field | Value |
|---|---|
| Project name | Automated Note-Making for `[Telecom Client]` |
| Project type | New initiative / Phase I |
| Project sponsor | `[Telecom Client]` |
| Primary driver | Mandatory / Efficiency |
| Division | IT |

## Stakeholders
| Role | Function |
|------|----------|
| Product Manager | Product retail |
| Operations Manager | Operations |
| Meeting Schedulers | Video conference team |
| Employees | End users |

## Dependencies
Voice-to-text during video conferencing is not a regular service — proper industry research required to pick the right API; filter system needed to shortlist options.

## Constraints & assumptions
**Constraints**
- **Time:** 3 months, team @ 8 hrs/day × 5 days/week
- **Cost:** Capped budget for dev + procurement
- **Scope:** May not fully cover identified scope

**Assumptions**
- Sponsor approved the proposal
- Funds available
- Feasibility study approved
- Speech adaptation customization viable
- Automatic conversion of spoken numbers → addresses / years / currencies via classes

## Functional requirements
- **Registration** — employees must register to enable the feature
- **Login** — via existing employee SSO
- **Logout** — at meeting end, automated email of transcribed notes sent to registered email
- **Report generation** — daily admin report of meetings with notes sent

## Non-functional requirements
1. Secure access to confidential data
2. 24×7 availability
3. Better component design for peak-time perf
4. Flexible service-based architecture for future extension

## MSCW prioritization
| Must | Should |
|------|--------|
| Translates speech → clear notes (EN UK/US) | Allow employees to record limited session within client + external org domain |
| Send automated email at session end | Speech adaptation |

| Could | Won't |
|-------|-------|
| Multiple sessions within a meet | Advanced additional languages |
| Desktop + mobile experience | Activities unrelated to notes |
| Full infra control + protected speech data on Google's speech tech | |

## User story
**Summary:** Automated Note Making MVP1 — Full XP
**Actor:** Employee

> As an Employee
> I want a "Text-to-Speech" button icon next to the recording icon in the existing video conferencing UI
> So that when clicked, a gray dot appears next to the recording icon (showing transcription is active) and on second click (or meeting end) the recorded speech is converted to text (.txt)
> And meeting notes are emailed to attendees within 30 minutes — containing Meet Title, Time, Attendees, Duration.

### Solution
- UI + backend dev for Text-to-Speech feature
- REST + service-ID auth → Google Cloud Speech-to-Text API (Postman URL + JSON)
- Embed in existing client system intent
- Automated email triggered at meeting end per SOP
- Code samples: https://cloud.google.com/speech-to-text/docs/samples

### Acceptance criteria
**Given** I am on the existing video conference page
**When** I click "Text-to-Speech", a gray dot appears near the recording icon (transcription active)
**Then** Meeting notes are sent within 30 minutes of meeting end, containing Meet Title, Time, Attendees, Duration.

## References
- https://blog.api.rakuten.net/top-10-best-speech-recognition-apis-google-speech-ibm-watson-speechapi-and-others/
- https://cloud.google.com/speech-to-text
- https://support.3playmedia.com/hc/en-us/articles/360033616834-Zoom-Integration-Setup
- https://nordicapis.com/5-best-speech-to-text-apis/
