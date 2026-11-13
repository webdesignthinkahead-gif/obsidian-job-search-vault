# Dashboard (Lite)

## Active pipeline
```dataview
TABLE WITHOUT ID file.link AS "Role", company AS "Company", status AS "Stage", applied AS "Applied", next_action AS "Next action", follow_up AS "Follow-up"
FROM #application AND -"Templates"
WHERE !contains(list("rejected", "ghosted", "withdrawn", "offer", "accepted"), status)
SORT follow_up ASC
```

## Follow-ups due
```dataview
TABLE WITHOUT ID file.link AS "Role", company AS "Company", next_action AS "Do this", follow_up AS "Due"
FROM #application AND -"Templates"
WHERE follow_up AND follow_up <= date(today) AND !contains(list("rejected", "ghosted", "withdrawn", "accepted"), status)
SORT follow_up ASC
```

---
**Want the full system?** The full *Job Search Vault* adds upcoming interviews, stage counts, a ghosting check and a "sources that work" analysis.
It also includes Interview, Contact, STAR Story and Weekly Review templates, plus 5 guides: follow-up scripts, interview question bank, salary negotiation, resume bullet formulas and a 30-day plan.
→ https://gumroad.com
