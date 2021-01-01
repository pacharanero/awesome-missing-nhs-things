# Awesome *Missing* Healthcare [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

* A curated, un-awesomelist of *Missing* NHS, Healthcare and Social Care interfaces, services, registers, and data sources.
* This is a 'partner' list to the Awesome Healthcare list https://github.com/kakoni/awesome-healthcare here I'm focusing on what's needed but conspicuously absent.

## National web services and APIs
* ['Gravatar' for patient photos](https://github.com/pacharanero/awesome-missing-nhs-things/issues/1)
* 'KeyBase' for clinical staff
* Ambulance Booking API
* [National Consent Platform]()
* REST API wrapper over the NHS E-Referral Service
* REST API wrapper over the NHS E-Prescriptions Service
* National Poisons Information Service ([TOXBASE](https://www.toxbase.org/)) as a REST API to allow embedding into clinical applications.

## Staff Registers
* GMC Register API - get information about practicing doctors programmatically, including information about specialist status. Real-time confirmation of current valid registration.
* NMC number API - get information about practicing nurses and midwives programmatically
* BCAP Register (counselling and psychotherapy) API
* Physios and other Musculoskeletal Therapists Register API
* Social worker registration API
* Speech and language therapists API

## Internal information services in hospital trusts, primary care and other care settings.
* Ubiquitous, versatile e-Rostering platform for staff rotas, with rota and on-call lists available via API to allow other applications to be aware of the current on-call clinician for a speciality, with appropriate fall-backs. Having that information available as an API is an important upstream dependency for a lot of useful services in automatic referral, time-saving features in EPRs (eg automatic selection of the correct consultant team for test ordering), and bleep replacement.

## Locations Registers
* ODS Code API (this now exists following work by Matt Stibbs and Tony Yates to build openODS)
* GP Practices register API
* Pharmacies register API
* Independent care providers API

## Health 'MapIt'
* MapIt by MySociety simplifies the use of geospatial information and enables easy creation of map layers or overlays reflecting open data and administrative boundaries
* Layer: CCG Boundaries
* Layer: GP Practice Boundaries
* Layer: Mapping of open data about ‘X’ health condition
* Layer: Location of GP practices
* Layer: Location of Hospitals
* Location of Urgent Care Centres

## Clinical Calculation APIs
* comprehensive, clinically assured, clinical calculation APIs
  * there are thousands of clinical assessment tools which we use to help make clinical decisions
  * these should all be available behind validated, clinically-assured APIs
  * this would improve the availability of these tools
  * comprehensive, clinically assured, clinical decision support API
* building these as APIs creates a 'library' of clinical support which developers can easily add to their applications
* without such service APIs, the clinical and technical assurance required to add them becomes too much.
* (how many websites had mapping before Google Maps? yet how easy is it to add a map now?)
* Also, when systems have to implement all these calculations separately and repeatedly and at huge expense - it is hugely wasteful. The eventual end payer for health tech is the **patient** (whether as taxpayer in a public service, or directly in a private service), and we can provide better value by doing these things **once** and sharing it.

## NHS As A Platform 
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
* REST wrapper for all Spine services, doing the hard work to make it simple. The madness of CDA, HL7 and MESH needs to be hidden from view. (this work is in progress [here](https://digital.nhs.uk/developer))

## Frameworks and Libraries
* NHS Common User Interface (or the good bits of it) implemented as a CSS-class-based web UI framework that can be dropped into new or existing web applications, lending them an instant UI which is ready clinically-, usability- and accessibility-tested.
* [The NHS Frontend Framework](https://github.com/nhsuk/nhsuk-frontend) admirably shows how this works in practice, but their focus is in creating nice, accessible, NHS websites. We need to take this principle and start sharing the UI components of good clinical software.


## Data gathering and Intelligence
* NHS PC Benchmarking - a downloadable open source software agent which benchmarks the PC being used and reports back to a central authority via web on: installed OS, patch level, RAM, CPU, disk, installed software, network bandwidth, and other information that would help national IT resources to be distributed in the most effective way possible.

## Open Source NHS Staff Online Training platform
* NHS staff undergo regular (usually annual) retraining on topics such as:
  * Child and Adult Safeguarding
  * Infection Control and Hand Hygiene
  * Lifting and Handling
  * Information Governance and Computer Security
* At present this is usually provided through a series of [proprietary online training modules](https://www.bluestreamacademy.com/), often of [very low quality](https://twitter.com/marcus_baw/status/1113058212150829059), and provided by a number of private companies at at least moderate taxpayer expense. The *content* for the platforms has quite often been originally provided (in some convoluted way eg a 'partnership') by NHS staff themselves and therefore paid for by UK taxes.
* The requirement for a simple, high-quality, modern e-Learning platform for the NHS would be relatively easy to fulfil compared to some of the other awesomely-missing things on this list, and would save considerable money.

-----

###### This repository and list is licensed under Creative Commons CC-BY-SA 3.0 https://creativecommons.org/licenses/by-sa/3.0/
