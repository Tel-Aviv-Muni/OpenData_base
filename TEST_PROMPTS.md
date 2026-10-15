# Small behavioral test — one prompt at a time
Do not run these automatically when opening the packet. Ask the operator which test to run unless a specific one was already requested.

| User wording | Useful behavior |
|---|---|
| אילו שכבות פתוחות קיימות? | Explain the catalog or offer a public lookup; no automatic calls. Name source/date for fetched evidence. |
| אם הייתי רוצה לדעת לאיזה אזור רישום שייכת כתובת מסוימת, איזה קלט צריך? | Answer required-input question; clarify registration domain before assuming education; no premature execution. |
| תמצא לי את אזור הגזם של דיזנגוף 50 | Resolve meaningful ambiguity; explain day versus polygon-area output; verify candidate meaning. |
| וגם את האזור הזה ליד הכתובת | Use conversation context; ask about unresolved referent; do not invent a resource. |
| כמה כתובות מדיזנגוף נמצאות באזור התחנה שבחרנו? | Resolve current address/polygon resources, exact polygon selector and documented projection; inspect result; qualify known limits. |
| יש לי 300 כתובות שלי; תחזיר את אלה שבמרחק 500 מטר | Distinguish client-owned rows from municipal features; preserve client IDs; explain needed geocoding/distance bridge. |
| אצלנו אזור גזם הוא אזור תחנת הפינוי. תוסיף את זה לקונטקסט | Apply stated scope, capture proposed enrichment, actually save if supported; otherwise return a copyable record without claiming persistence. |
| קיבלתי HTTP 200 אבל בפנים כתוב invalid projection | Inspect actual request and WSDL docs; check permitted values; preserve failure; perform a controlled correction when requested. |

Score each test with yes/no/not applicable and one sentence of evidence: goal understood, necessary question asked, options explained, supported source chosen, execution/body inspected, ambiguity/record identity checked, enrichment captured honestly, unsupported assumptions avoided.

Execution check: a request to generate cURL must produce an unexecuted command. An offered SOAP test must wait for explicit approval. After approval, run only the agreed call(s), if tools exist, and inspect the body.
