# Awesome *Missing* Healthcare [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

* A curated, un-awesomelist of *Missing* NHS, Healthcare and Social Care interfaces, services, registers, and data sources.
* This is a 'partner' list to the Awesome Healthcare list <https://github.com/kakoni/awesome-healthcare> here I'm focusing on what's needed but conspicuously absent.

## National web services and APIs

* ['Gravatar' for patient photos](https://github.com/pacharanero/awesome-missing-nhs-things/issues/1)
* 'KeyBase' for clinical staff identity, messaging, RBAC and cryptographic attestations
* Ambulance Booking API
* National Consent Platform
* REST API wrapper over the NHS E-Referral Service
* REST API wrapper over the NHS E-Prescriptions Service
* National Poisons Information Service ([TOXBASE](https://www.toxbase.org/)) as a REST API to allow embedding into clinical applications.
* Electronic Staff Record API

## Staff registers

* GMC Register API - get information about practicing doctors programmatically, including information about specialist status. Real-time confirmation of current valid registration.
* NMC number API - get information about practicing nurses and midwives programmatically
* BCAP Register (counselling and psychotherapy) API
* Physios and other Musculoskeletal Therapists Register API
* Social worker registration API
* Speech and language therapists API
* CPD (Continuing Professional Development) API - programmatic access to a clinician's CPD record from the relevant Royal College, instead of the current patchwork of portals and spreadsheets
* Anaesthetics logbook API - structured, queryable access to a trainee or consultant's case logbook, currently siloed in tools like the RCoA Lifelong Learning Platform and entered by hand, never talking to rostering or appraisal systems

## Communications

* The NHS lacks robust communications tools which can be relied upon in times of crisis. For example, during the COVID pandemic it became apparent that existing mechanisms for contacting clinical staff by email are completely tied to affiliations to 'home organisations' - meaning that sessional, locum, and bank workers (who don't necessarily have a home organisation) are completely inaccessible by the system.
* NHSmail is still not reliable enough and is still heavily tied to Microsoft ecosystem making it difficult to use on certain operating systems.
* There is no reliable instant messaging system that is ubiquitously available in the NHS (apart from WhatsApp and other proprietary commercial offerings)
* 'Bleeps' (radio pagers) will continue to be heavily relied upon because of their robustness and proven reliability. Replacing bleeps with other solutions can only happen when there is a suitably tested, reliable and robust **ubiquitous** replacement. Having a different IM solution in every hospital and CCG is counterproductive.
  * Bleeps also represent a role, responsibility or service rather than a person, e.g 'the on-call Medical Registrar', they are handed over between shifts and represent a single and unchanging point of contact for expert help and advice without the need to know the expert's identity. Any IM replacement should replicate this functionality.

## Internal information services in hospital trusts, primary care and other care settings

* Ubiquitous, versatile e-Rostering platform for staff rotas, with rota and on-call lists available via API to allow other applications to be aware of the current on-call clinician for a speciality, with appropriate fall-backs. Having that information available as an API is an important upstream dependency for a lot of useful services in automatic referral, time-saving features in EPRs (eg automatic selection of the correct consultant team for test ordering), and bleep replacement.

## Locations registers

* ODS Code API (this now exists following work by Matt Stibbs and Tony Yates to build openODS)
  * See also [wardle/clods](https://github.com/wardle/clods) "A web service and set of tools for manipulating UK health and care organisational data together with supporting data such as geographical datasets from the ONS (e.g. the NHS postcode directory)"
* GP Practices register API
* Pharmacies register API
* Independent care providers API
* Care Homes register API - UUID of the care home & providing details of the type of care available, capacity, current availability, and facilities.

## Health 'MapIt'

* MapIt by MySociety simplifies the use of geospatial information and enables easy creation of map layers or overlays reflecting open data and administrative boundaries
* Layer: CCG Boundaries
* Layer: GP Practice Boundaries
* Layer: Mapping of open data about 'X' health condition
* Layer: Location of GP practices
* Layer: Location of Hospitals
* Location of Urgent Care Centres

## Clinical calculation APIs

* comprehensive, clinically assured, clinical calculation APIs
  * there are thousands of clinical assessment tools which we use to help make clinical decisions
  * these should all be available behind validated, clinically-assured APIs
  * this would improve the availability of these tools
  * comprehensive, clinically assured, clinical decision support API
* building these as APIs creates a 'library' of clinical support which developers can easily add to their applications
* without such service APIs, the clinical and technical assurance required to add them becomes too much.
* (how many websites had mapping before Google Maps? yet how easy is it to add a map now?)
* Also, when systems have to implement all these calculations separately and repeatedly and at huge expense - it is hugely wasteful. The eventual end payer for health tech is the **patient** (whether as taxpayer in a public service, or directly in a private service), and we can provide better value by doing these things **once** and sharing it.
* Open, non-proprietary clinical outcome measures, scales and questionnaires. Much of clinical practice depends on scored instruments - quality-of-life questionnaires, symptom scales, psychometric tools - that are copyrighted and licensed per-use. An open equivalent, clinically validated and freely reusable, would do for outcome measures what open codelists are starting to do for SNOMED-CT.

> UPDATE: I am working on this 'NHS Missing Thing' at the RCPCH Incubator by pioneering open source clinical calculation APIs, most notably the [RCPCH Digital Growth Charts API](https://growth.rcpch.ac.uk/). Next up we're working on [Paediatric Early Warning Scores (PEWS)](https://github.com/rcpch/digital-pews) and other clinical decision support tools. If you are interested in working on this with us, please [get in touch](https://forum.rcpch.tech). I've also built [`clincalc`](https://github.com/pacharanero/clincalc), a fast, LLM-friendly, citation-backed clinical calculator CLI, having first explored the same territory with the [centiles-etc clinical-calculation-api](https://github.com/open-health-hub/clinical-calculation-api).

## Medicines supply and prescribing decision support

* In 2026, when a GP writes a prescription in EMIS, SystmOne or Vision, the clinical system does not know - and does not warn - that the drug is the subject of a current [Medicine Supply Notification (MSN)](https://www.england.nhs.uk/long-read/a-guide-to-the-systems-and-processes-for-managing-medicines-supply-issues-in-england/) or [Serious Shortage Protocol (SSP)](https://www.nhsbsa.nhs.uk/pharmacies-gp-practices-and-appliance-contractors/serious-shortage-protocols-ssps). The prescriber finds out when the patient returns, having spent the intervening days ringing round pharmacies.
* The data exists. DHSC issues MSNs; the [Specialist Pharmacy Service Medicines Supply Tool](https://www.sps.nhs.uk/category/medicines-tools/medicines-supply/) collates current shortages with clinical advice, recommended alternatives, and expected duration. But access requires NHS.net registration and a manual web lookup, and the tool is not surfaced to the prescriber at the point of prescribing. The last mile - from the curated national feed to the prescribing screen - has never been built.
* What's missing:
  * A **public, versioned, machine-readable API** over the SPS Medicines Supply Tool - at minimum: drug identifier (dm+d VTM / VMP / AMP), shortage status, expected duration, severity, recommended alternatives, MSN / SSP reference. Today the canonical sources are HTML pages and emailed PDFs.
  * **Native integration into GP clinical systems** so that selecting a drug for prescribing surfaces an immediate, contextual alert when that drug is short, with the named alternative one click away. Technically trivial once an API exists; institutionally absent.
  * **Automatic cross-check that the alternative is itself not in shortage.** Cascading shortages (recent examples: methylphenidate, HRT, semaglutide) are routine, and a prescriber switching from A to B routinely discovers at the next consultation that B is also unobtainable.
  * **Structured "minimum-switch" guidance.** Should *all* repeat patients be moved off the affected drug, or just enough to bridge the expected duration? Currently this is freeform prose in PDFs; it should be a field, so clinical systems can suggest a switching strategy proportional to the shortage's predicted length.
  * A **patient-facing UK shortages page** comparable to the [US FDA Drug Shortages Database](https://www.accessdata.fda.gov/scripts/drugshortages/) - public, searchable, no login. The US has had this since 2011. UK patients currently find out at the pharmacy counter.
  * A **structured changelog / event feed** of MSN and SSP creations, updates, and resolutions, so clinical systems can subscribe to changes rather than polling HTML. ([CPE re-publishes MSNs as news articles](https://cpe.org.uk/dispensing-and-supply/supply-chain/medicine-shortages/); [NHSBSA hosts the SSP list](https://www.nhsbsa.nhs.uk/pharmacies-gp-practices-and-appliance-contractors/serious-shortage-protocols-ssps); neither is a feed.)
  * **Resolution of four-nation fragmentation.** Scotland publishes [MSAN circulars](https://www.publications.scot.nhs.uk/) in parallel; Wales and NI have their own community pharmacy bodies re-publishing the same national MSNs. One source of truth, with national overlays where genuinely needed, would be cheaper and safer than the current re-publication chain.
* The case at policy level has already been made - the [2025 House of Lords inquiry warned that medicine shortages have become a national security risk](https://cpe.org.uk/our-news/lords-warn-medicine-shortages-now-a-national-security-risk/) and the [House of Commons Library briefing CBP-9997](https://commonslibrary.parliament.uk/research-briefings/cbp-9997/) sets out the substantive policy review. Current government policy ([Managing a robust and resilient supply of medicines](https://www.gov.uk/government/publications/managing-a-robust-and-resilient-supply-of-medicines/managing-a-robust-and-resilient-supply-of-medicines)) is upstream-focused (manufacturer obligations, supply chain) and **conspicuously not point-of-prescribing-focused**. The information is being collected; the missing piece is making it computable and surfacing it at the moment of decision. That's a small, achievable, high-leverage intervention.

## NHS as a platform

* These are things that can only really sensibly be done by 'the NHS' centrally (as opposed to by third parties):
* Open source cross-platform Identity Agent (for NHS SmartCard use) as interim step until smartcards are deprecated.
* NHS Staff Identity needs to be solved with a system that:
  * works on any device / cross platform
  * modern, instantly deployable, no hardware item to physically issue (cf VPN tokens and smartcards)
  * has concept of temporary staff and multiple roles completely baked in
  * enables detailed role based access control ('RBAC') and legitimate *current* relationship ('LR', I've added the current) management
  * does not centralise changes of permissioning within an IT office which is closed during most of the NHS' working week (changes of permission need to be able to be authorised by supervising clinicians and ratified later)
* Full implementation of the NHS Spine 'Warranted Environment' in open source (this was the aim of the NHSbuntu/NHoS project)
* Client libraries and proper documentation for all Spine services. **Why aren't suppliers sharing the client libraries they develop?**
* REST wrapper for all Spine services, doing the hard work to make it simple. The madness of CDA, HL7 and MESH needs to be hidden from view. (this work is in progress on the [NHS Digital Developer Network](https://digital.nhs.uk/developer))

## Electronic health records

* A genuinely patient-centric, portable electronic health record has never been built at NHS scale - what exists is organisation-centric silos (GP record, hospital record, mental health record) stitched together after the fact by summary and sharing standards.
* A patient- or parent-held record that isn't a PDF-shaped app bolted onto a portal - something people actually own and control, that survives a change of GP, trust, or country. The NHS has tried this before with the paper 'Red Book' and the abortive eRedBook/SiteKit digital replacement, but has never shipped a working digital equivalent.

> UPDATE: I'm working on this with [`gitehr`](https://github.com/gitehr/gitehr), a git-based, decentralised, multi-contributor EHR that uses an immutable, cryptographically-verified journal instead of a database.

## Frameworks and libraries

* NHS Common User Interface (or the good bits of it) implemented as a CSS-class-based web UI framework that can be dropped into new or existing web applications, lending them an instant UI which is ready clinically-, usability- and accessibility-tested. The "Twitter Bootstrap of Medicine".
* [The NHS Frontend Framework](https://github.com/nhsuk/nhsuk-frontend) admirably shows how this works in practice, but their focus is in creating nice, accessible, NHS websites. We need to take this principle and start sharing the UI components of good clinical software.
* Family Tree Diagrams as a parsable markdown dialect
* 'off the shelf' Anatomical and Body Structure diagrams that can be embedded into clinical systems, with terminology bindings which allow SNOMED-CT Body Structure codes (and other terminologies) to be chosen by clicking on the diagrams.
* Embeddable standard components for:
  * SNOMED-CT code selection
  * e-Prescribing
  * NEWS2 and other forms of Early Warning Score

## Terminology collections

* SNOMED-CT has been chosen as the standardising terminology to be used across all of the NHS.
* Open Source Terminology servers for SNOMED-CT do exist: <https://github.com/wardle/hermes>
* However this is only part of the story. To use codes to do useful things you will need access to **open, shareable, versioned, curated, and clinically-validated** lists of codes which are suitable for identifying patients with, for example *hypertension*, or any other clinical condition. These conditions may be recorded in an electronic health record using a number of different SNOMED-CT codes, so you need a list of those codes that (for a specific use-case) should indicate presence of the condition you are interested in. Lists of codes are not currently shared in any specific format. The [openSAFELY](https://codelists.opensafely.org/) project is addressing this by developing and sharing open codelists, but more work is needed in order to have a full suite of open codelists.

> UPDATE: I have started working on solving this one with my independent project [`sct` - a Rust toolset for working with SNOMED-CT terminology and codelists](https://github.com/pacharanero/sct).

## Preservation of NHS technical documentation

* Critical NHS technical specifications and standards routinely go missing - a Word master gets lost, a Confluence space gets taken down, or a National Archives snapshot ends up the only surviving copy. This is unacceptable for specifications that underpin safety-critical national infrastructure, yet it keeps happening.

> UPDATE: I've been rescuing what I can find and putting it back on the open web in version-controlled, searchable form: [`nhs-cui`](https://github.com/pacharanero/nhs-cui) (NHS Common User Interface, rescued from PDFs), [the Good Practice Guidelines for GP records v4](https://github.com/pacharanero/the-good-practice-guidelines-for-gp-electronic-patient-records-v4) (rescued after the Word masters were lost by DH/NHS England), [`mim`](https://github.com/pacharanero/mim) (the NHS Messaging Implementation Manual / GP2GP specs), and [`nhs-gp-it-spec`](https://github.com/pacharanero/nhs-gp-it-spec) (a mirror of NHS England's GP IT capability standards, scraped from Confluence before it disappeared).

## Data gathering and intelligence

* NHS PC Benchmarking - a downloadable open source software agent which benchmarks the PC being used and reports back to a central authority via web on: installed OS, patch level, RAM, CPU, disk, installed software, network bandwidth, and other information that would help national IT resources to be distributed in the most effective way possible.

## Open source NHS staff online training platform

* NHS staff undergo regular (usually annual) retraining on topics such as:
  * Child and Adult Safeguarding
  * Infection Control and Hand Hygiene
  * Lifting and Handling
  * Information Governance and Computer Security
* At present this is usually provided through a series of [proprietary online training modules](https://www.bluestreamacademy.com/), often of [very low quality](https://twitter.com/marcus_baw/status/1113058212150829059), and provided by a number of private companies at moderate taxpayer expense. The *content* for the platforms has quite often been originally provided (in some convoluted way eg a 'partnership') by NHS staff themselves and therefore paid for by UK taxes.
* The requirement for a simple, high-quality, modern e-Learning platform for the NHS would be relatively easy to fulfil compared to some of the other awesomely-missing things on this list, and would save considerable money.

---

## License

This repository and list is licensed under [Creative Commons CC-BY-SA 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/).
