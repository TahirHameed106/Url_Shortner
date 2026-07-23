# URL Shortener — Learning Project

A backend engineering project built from scratch to learn REST APIs, databases,
unique ID generation, redirects, and (eventually) production concerns like
caching, rate limiting, and deployment.

**Stack:** C# + ASP.NET Core Web API · SQL database via Entity Framework Core (TBD: SQL Server / PostgreSQL / SQLite)
**Rule of the project:** No AI-generated code. Design decisions and implementation
are mine. AI is used only as a mentor to ask questions and review finished work.

> Note: this project originally started in Node.js + Express (MERN). It was
> re-platformed to .NET for job-market reasons. The six phases below and the
> underlying concepts (HTTP, REST, schema design, redirects, caching) carry
> over unchanged — only the language and framework layer changed.

---

## Progress tracker

- [ ] C# / OOP prep (classes, properties, constructors, inheritance, interfaces)
- [ ] Phase 1 — MVP (create, redirect, get details)
- [ ] Phase 2 — Database schema design
- [ ] Phase 3 — Short code generation strategy
- [ ] Phase 4 — Redirect logic, edge cases
- [ ] Phase 5 — Production design decisions
- [ ] Phase 6 — Advanced features

---

## Prerequisite: C# / OOP fundamentals

Work through these before Phase 1, each with a small standalone exercise —
don't skip straight to the web API.

- [ ] Classes & objects (blueprint vs. instance)
- [ ] Fields vs. properties (`get` / `set`, auto-properties)
- [ ] Constructors
- [ ] Methods
- [ ] Access modifiers (`public`, `private`, `protected`)
- [ ] Encapsulation
- [ ] Inheritance
- [ ] Polymorphism
- [ ] Interfaces
- [ ] Abstract classes
- [ ] `async`/`await` and `Task<T>`

**Notes / sticking points to revisit:**
-

---

## Phase 1 — MVP

Three endpoints only. No auth, no caching, no extras.

| Method | Route | Purpose |
|---|---|---|
| POST | `/shorten` | Create a short URL from a long one |
| GET | `/{code}` | Redirect to the original URL |
| GET | `/urls/{code}` | Return original URL, created date, click count |

In ASP.NET Core these will live as action methods inside a Controller class —
research `[ApiController]`, `[Route]`, `[HttpGet]`/`[HttpPost]` attributes
yourself before writing one.

**Definition of done:** all three endpoints work against a running local
database, tested manually (curl / Postman / Thunder Client).

---

## Phase 2 — Database schema

Answer these *before* writing a model class or a `CREATE TABLE` statement:

1. What columns does the `Url` entity need for Phase 1 only?
2. Which column is the unique constraint, and why?
3. What data type is `ClickCount`, and what's its default?
4. What indexes does this table need, and what query justifies each one?

**My schema attempt (C# entity class):**

```csharp
// write your Url class here once you've reasoned it out
// e.g. public class Url { public int Id { get; set; } ... }
```

**Database choice:** _(fill in once decided — SQL Server / PostgreSQL / SQLite, and why)_
**ORM choice:** _(Entity Framework Core / Dapper, and why)_

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

1. Request arrives at `GET /{code}`
2. Look up `code` in the database
3. If found → increment click count → issue redirect
4. If not found → return 404
5. Decide: 301 or 302? Look up `RedirectResult` vs `RedirectPermanent` in ASP.NET Core.

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

- [ ] User accounts (ASP.NET Core Identity)
- [ ] Custom aliases (`/tahir`)
- [ ] Expiring links
- [ ] Password-protected links
- [ ] QR code generation
- [ ] Analytics dashboard
- [ ] Redis caching
- [ ] Rate limiting
- [ ] Docker
- [ ] CI/CD
- [ ] Logging (Serilog)
- [ ] Monitoring (Application Insights / OpenTelemetry)
- [ ] Unit and integration tests (xUnit)

---

## Local setup (fill in as the project grows)

```bash
# create the web api project
dotnet new webapi -n UrlShortener
cd UrlShortener

# run
dotnet run
```

Connection strings, EF Core migrations, and environment config go here
as they're introduced — don't pre-fill this before you need it.

---

## Notes / questions for mentor review

Use this space to log things to bring back for review — schema drafts,
"why is my redirect returning 404" type bugs, or design decisions you're
unsure about.

-
