# URL Shortener — Learning Project

A backend engineering project built from scratch to learn REST APIs, databases,
unique ID generation, redirects, and (eventually) production concerns like
caching, rate limiting, and deployment.

**Stack:** Node.js + Express · Database TBD (see Phase 2)
**Rule of the project:** No AI-generated code. Design decisions and implementation
are mine. AI is used only as a mentor to ask questions and review finished work.

---

## Progress tracker

- [ ] Phase 1 — MVP (create, redirect, get details)
- [ ] Phase 2 — Database schema design
- [ ] Phase 3 — Short code generation strategy
- [ ] Phase 4 — Redirect logic, edge cases
- [ ] Phase 5 — Production design decisions
- [ ] Phase 6 — Advanced features

---

## Phase 1 — MVP

Three endpoints only. No auth, no caching, no extras.

| Method | Route | Purpose |
|---|---|---|
| POST | `/shorten` | Create a short URL from a long one |
| GET | `/:code` | Redirect to the original URL |
| GET | `/urls/:code` | Return original URL, created date, click count |

**Definition of done:** all three endpoints work against a running local
database, tested manually (curl / Postman / Thunder Client).

---

## Phase 2 — Database schema

Answer these *before* writing a `CREATE TABLE` statement:

1. What columns does the `urls` table need for Phase 1 only?
2. Which column is the unique constraint, and why?
3. What data type is `click_count`, and what's its default?
4. What indexes does this table need, and what query justifies each one?

**My schema attempt:**

```sql
-- write your CREATE TABLE statement here once you've reasoned it out
```

**Database choice:** _(fill in once decided — Postgres / SQLite / other, and why)_

---

## Phase 3 — Short code generation

Research and compare before picking one:

- Base62 encoding of an auto-increment ID
- Random string generation
- UUID
- NanoID

**Decision + reasoning:**
_(write 2–3 sentences on which approach you chose and the tradeoff that convinced you)_

---

## Phase 4 — Redirect logic

Trace the full sequence by hand before coding it:

1. Request arrives at `GET /:code`
2. Look up `code` in the database
3. If found → increment click count → issue redirect
4. If not found → return 404
5. Decide: 301 or 302? Why?

**My redirect status code choice + reasoning:**
_(write it here)_

---

## Phase 5 — Design questions to answer on paper

- What if two users generate the same code? How do I prevent or detect it?
- What if someone shortens the same URL twice — new code, or return the existing one?
- How long should a short code be, and what does that length buy me?
- Should codes expire? What happens to a redirect after expiration?

---

## Phase 6 — Advanced features (one at a time)

For each feature, answer before building:
1. What problem am I solving?
2. What data do I need?
3. What API should expose this?

- [ ] User accounts
- [ ] Custom aliases (`/tahir`)
- [ ] Expiring links
- [ ] Password-protected links
- [ ] QR code generation
- [ ] Analytics dashboard
- [ ] Redis caching
- [ ] Rate limiting
- [ ] Docker
- [ ] CI/CD
- [ ] Logging
- [ ] Monitoring
- [ ] Unit and integration tests

---

## Local setup (fill in as the project grows)

```bash
# clone / init
npm init -y
npm install express

# run
node index.js
```

Environment variables, database connection string, and run scripts go here
as they're introduced — don't pre-fill this before you need it.

---

## Notes / questions for mentor review

Use this space to log things to bring back for review — schema drafts,
"why is my redirect returning 404" type bugs, or design decisions you're
unsure about.

-
