# Landis+Gyr

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Landis+Gyr Group AG is a 130-year-old energy technology company that builds the smart electricity, gas and water meters, the RF-mesh and cellular networks, and the head-end, meter-data-management and grid-analytics software that utilities run advanced metering infrastructure on. It is incorporated in Cham, Switzerland and listed on the SIX Swiss Exchange (ticker `LAND`), with its Americas headquarters — and much of its executive team — in Alpharetta, Georgia.

After divesting its EMEA business to AURELIUS in 2026, the company states it will "sharpen its strategic focus on the Americas and Asia-Pacific regions". The United States is its home market. It serves "more than 2,000 utilities worldwide".

Home market: **United States** · Tier: **metering** · https://www.landisgyr.com/us/en/home

## Where it sits in the value chain

One layer **upstream of the consumer**. Landis+Gyr sells to the utilities that are themselves the regulated data holders. The meter it manufactures creates the most granular consumer energy data in existence — and Landis+Gyr ships none of it to the public.

## Mandate posture

| | |
|---|---|
| Mandate regime | **none** |
| Mandate status | **not-applicable** |
| Data standard (consumer) | **no standard reference found** |
| Data standard (network) | Wi-SUN FAN (15 certified products), IPv6 mesh |
| Consumer data API | **no** |
| Open market / grid data | **no** |

Green Button (NAESB/NIST ESPI) obligations attach to utilities and retailers, not to meter manufacturers — and in the US the programme is voluntary with nothing compelling adoption. Ontario's Green Button regulation binds Ontario LDCs. Australia's Consumer Data Right for energy designates retailers and AEMO. Landis+Gyr sells into all three markets and is bound by none of them.

There is **no** Green Button page on the corporate site (all 425 sitemap URLs checked), **no** Landis+Gyr entry found in the Green Button Alliance platform-provider directory, and **no** Green Button claim made by the company. Where reporting describes Landis+Gyr meters producing ESPI XML, the export runs through a utility's own certified portal — a downstream implementation, not this company's.

## API surface

Landis+Gyr publishes **no public API documentation, no OpenAPI/Swagger/AsyncAPI, no Postman collection, no SDK download and no endpoint reference**. `apis[]` in `apis.yml` is deliberately empty.

A real developer portal does exist at **https://developers.landisgyr.com/** — the Gridstream Connect Apps / Revelo edge-app program. It is:

- **Unlinked.** No page of the corporate site and no sitemap references it. The public call to action on the Gridstream Connect Apps Ecosystem page is "Email Our Team", pointing at a sales inquiry form.
- **Empty without auth.** `/get-started`, `/explore`, `/documents`, `/learning-paths`, `/community`, `/faq`, `/request-devkit`, `/dashboard` all return HTTP 200 and render nothing. Unknown routes 404, so those 200s are real routes.
- **Approval-gated.** The client bundle exposes `POST /register/validate/{id}`, an `/admin/users/invitations` surface, a per-page `access_list`, and an application-status enum including `APPROVED`.
- **Firebase-authenticated.** Google Identity Platform (`identitytoolkit.googleapis.com`) with reCAPTCHA Enterprise. `/.well-known/openid-configuration` → 404.

Getting in: register → pass validation/approval → request a Revelo developer kit at `/request-devkit`. Hardware or a simulated Revelo meter in App Studio is the actual unit of access; the "comprehensive set of APIs for meter app development" the marketing page advertises is an on-device Java app API, not a web API.

`developer.`, `docs.`, `api.` and `data.landisgyr.com` do not resolve. `github.com/landisgyr` is an individual's account, not the company.

## Artifacts

| Artifact | File | Wired in `apis.yml` |
|---|---|---|
| Company identity | `apis.yml` | — |
| Review — mandate, standards, consumer/market split, access gate, auth, probes, enrichment log | `review.yml` | — |
| Standards conformance — Wi-SUN FAN 1.0/1.1, IPv6 mesh, ISO management systems, MultiSpeak/CMEP | `conformance/landis-gyr-conformance.yml` | `Conformance`, `Compliance` |
| productCERT vulnerability disclosure programme | `security/landis-gyr-vulnerability-disclosure.yml` | `VulnerabilityDisclosure`, `Security` |
| TLS / HSTS / DNSSEC / CAA / SPF / DMARC probe | `security/landis-gyr-domain-security.yml` | `DomainSecurity` |
| Portfolio lifecycle + verified absence of versioning/deprecation/changelog/SLA/status page | `lifecycle/landis-gyr-lifecycle.yml` | `Lifecycle` |
| Package-registry sweep (8 registries, zero first-party libraries) | `packages/landis-gyr-packages.yml` | `Packages` |
| Generated llms.txt | `llms/landis-gyr-llms.txt` | `LLMsTxt` |
| `/.well-known/` sweep (30 probes, 6 hosts, all negative) | `well-known/landis-gyr-well-known.yml` | *withheld — nothing published* |
| Authentication profile (developer-portal Firebase; no API auth published) | `authentication/landis-gyr-authentication.yml` | *withheld — no documented API auth* |

No `openapi/` directory: nothing real was found to harvest, re-confirmed 2026-07-27 against
the API host roots, the docs host, and the Cloud Run backend the portal bundle exposes.

Two artifacts are deliberately **not** pointed at from `apis.yml`. Both would satisfy a
scored discoverability check (`WellKnown`, `Authentication`) that Landis+Gyr does not
actually earn — it publishes no `/.well-known/` document and documents no API
authentication. The files are kept as evidence of the sweep, not as claims.

## What Landis+Gyr does publish

Round two found more than round one did. Landis+Gyr runs a real coordinated vulnerability
disclosure programme — **productCERT**, `productCERT@landisgyr.com`, with a published PGP
key and a Vulnerability Management Policy Summary — and a real **certificate register**
carrying ISO/IEC 27001, ISO 9001, ISO 14001, ISO 45001 and ISO 22301 with downloadable
PDFs. It has certified products to **Wi-SUN FAN 1.1** as well as 1.0. And Oracle Utilities'
adapter documentation reveals that the Gridstream Command Center head-end speaks
**MultiSpeak v3.1** and **CMEP** — the first concrete evidence of the protocol behind the
gate, though it is an integrator's description rather than a Landis+Gyr publication.

The security and quality posture is well documented. The API posture is not documented at
all. That gap is the story.
