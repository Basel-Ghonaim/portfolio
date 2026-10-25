# 07 — Contact Channels

**Status:** Approved
**Approved on:** 2026-10-24

## Context

The contact form is deferred (D2-04). First-release channels are email, WhatsApp, LinkedIn, and GitHub, managed from the dashboard (D2-11). Contact data has a single source (D3-06).

## Decisions

| ID | Decision | Rationale |
|---|---|---|
| D7-01 | This axis is renamed from "Contact and messages" to "Contact channels". | Reflects its actual scope after deferring the contact form. |
| D7-02 | The "Contact me" action takes the visitor to the homepage Contact section, which lists all channels. From any other page, it opens the homepage at that section. It does not open email directly. | Shows every channel instead of forcing one, and avoids silent failure for visitors without a configured mail client. |
| D7-03 | Channel placement: the Contact section shows all visible channels with name and value, plus a "copy email" action. The footer on every page shows all visible channels as icons. The Hero shows only the "Contact me" and CV actions, with no channels. Channel order is set manually; each channel can be shown or hidden. | Channels are always reachable without cluttering the first screen. |
| D7-04 | WhatsApp opens with a prefilled message in the language of the current page. The message is managed in both languages from the dashboard, and the visitor can edit it before sending. | Lowers the effort of starting a conversation. This message is bilingual content under D6-04. |
| D7-05 | Copying the email shows a short "Copied" confirmation in the page language, announced to screen readers. | Clear feedback for all visitors, including screen-reader users. |

## Decisions from the consistency review (2026-10-24)

| ID | Decision | Rationale |
|---|---|---|
| D7-06 | Contact channels are chosen from a predefined list of supported channel types (e.g. email, WhatsApp, LinkedIn, GitHub, X, Telegram). Each type has its own design icon and an interface label in both languages. The owner adds the value and manages order and visibility. A type not in the list requires a small code addition. Refines D2-11 and corrects the channel-name row of the D6-03 classification. *(Review C-02.)* | Footer icons are part of the design (D7-03, D8-01) and Arabic pages need Arabic channel labels; arbitrary channel types could not provide either. |

## Carried forward

- Counting clicks per contact channel → axis 09 (analytics).
