# Tableflipper Notes

Temporary working notes for the development of the Tableflipper workflow.

## Reference material

Methodologies, templates, tools, etc. that can potentially be used to back the different phases and aspects of the workflow. The focus is on material that can be bundled and distributed with the workflow (as opposed to being accessed by URL while the workflow is running). Copyrighted material is not bundled as-is, but relevant information is manually derived and bundled instead. Non-executable reference material should be bundled and vendored in plain text format.

### Requirements engineering process

- Volere
- IREB CPRE handbooks (TODO: what is really in them?)
- SWEBOK (Chapter 01: Software Requirements)
- Karl Wiegers

### Requirements document format

- Volere
- req42

### Quality model

- Q42
- Volere (non-functional requirement types)
- ISO 25010
- SEI "Software Architecture in Practice" (quality model also described on <https://quality.arc42.org/articles/sei-quality-model>)
- TODO: FURPS+ (<https://web.archive.org/web/20201112020231/http://www.ibm.com/developerworks/rational/library/4706.html>)
- TODO: check for other quality models on <https://quality.arc42.org/references/> and <https://quality.arc42.org/articles/quality-models>

### Architecture methodology

- TODO: Risk-driven architecture
- TODO: Attribute-driven design
- TODO: Patterns 42
- TODO: check for more among 1790375541.md (Software engineering books in owl-data)
  - For example, Viewpoints and Perspectives (Rozanski and Woods), Design It! (Keeling), Continuous Architecture, Evolutionary Architecture, Domain-Driven Design

### Architecture documentation

- arc42
- Software guidebook
- TODO: explore more (e.g. 4+1 architectural view model, Views and Beyond, Viewpoints and Perspectives (Rozanski & Woods), ISO/IEC/IEEE 42010)

### Architecture Decision Record (ADR) format

- Nygard
- MADR
- TODO: see other formats in 1783081987.md (Architecture Decision Records in owl-data)

### Architecture Decision Record (ADR) management

- TODO: adr-tools, Log4brains, Decision Guardian, Mneme (see 1783081987.md in owl-data)

### Architecture diagrams

- C4
- Structurizr
- LikeC4
- TODO: evaluate diagram-as-code solutions (Mermaid, PlantUML, etc.)

### Development methodology

- TODO: Walking skeleton
- TODO: Test-driven development
- TODO: Spec-driven development
- TODO: explore more

### References

- Volere
  - Website: <https://www.volere.org/>
  - Template (paid): <https://www.volere.org/templates/volere-requirements-specification-template/>
  - Books
    - Mastering the Requirements Process, 4th edition, 2024: <https://www.amazon.com/dp/0137969503>
    - Mastering the Requirements Process, 3rd edition, 2013: `mastering-the-requirements-process-3rd-edition-2013.pdf`
- req42
  - Website: <https://req42.de/>
  - Template: <https://github.com/Hruschka/req42-framework/raw/main/dist/req42-framework-EN-withhelp-markdown.zip>
- IREB CPRE handbooks 
  - CPRE Foundation Level Handbook: `cpre-foundation-level-handbook-v1.3.2.pdf`
  - CPRE Requirements Elicitation Handbook: `cpre-requirements-elicitation-handbook-v2.2.0-2025.pdf`
  - CPRE Requirements Modeling Handbook: `cpre-requirements-modeling-handbook-v2.2.0-2024.pdf`
  - CPRE Requirements Management Handbook: `cpre-requirements-management-handbook-v2.1.0-2024.pdf`
  - CPRE RE@Agile Handbook: `cpre-re-agile-handbook-v2.2.0-2025.pdf`
- SWEBOK (v4.0a): `guide-to-the-software-engineering-body-of-knowledge-swebok-v4.0a-2026.pdf`
- Karl Wiegers
  - Software Requirements, 3rd edition 2013: <https://www.amazon.com/dp/0735679665>
  - Software Requirements Essentials, 1st edition, 2023: `software-requirements-essentials-2023.pdf`
- Q42
  - Website: <https://quality.arc42.org/>
  - Articles: <https://quality.arc42.org/articles/>
  - GitHub: <https://github.com/arc42/quality.arc42.org-site>
- ISO 25010
  - ISO/IEC 25010:2023 (Product quality model): <https://www.iso.org/standard/78176.html> (paid)
  - ISO/IEC 25002:2024 (Quality model overview and usage): <https://www.iso.org/standard/78175.html> (free)
  - ISO/IEC 25019:2023 (Quality-in-use model): <https://www.iso.org/standard/78177.html> (paid)
- SEI "Software Architecture in Practice"
  - Software Architecture in Practice, 4th edition, 2021: <https://www.amazon.com/dp/0136886094>
  - Software Architecture in Practice, 3rd edition, 2012: `software-architecture-in-practice-3rd-edition-2013.pdf`
- Nygard
  - Template: <https://github.com/architecture-decision-record/architecture-decision-record/tree/main/locales/en-001/templates/decision-record-template-by-michael-nygard>
  - Article: <https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions>
- MADR
  - Templates: <https://github.com/adr/madr>
- Structurizr
  - Website: <https://structurizr.com>
  - Docs: <https://docs.structurizr.com/>
  - GitHub: <https://github.com/structurizr/structurizr>
- LikeC4
  - Website: <https://likec4.dev/>
  - Docs: <https://likec4.dev/tutorial/>
  - GitHub: <https://github.com/likec4/likec4>
- C4
  - Website: <https://c4model.com/>
  - Books
    - The C4 Model: Visualizing Software Architecture, 1st edition, 2026: <https://www.amazon.com/dp/B0GC5YKYFD>
    - The C4 model for visualising software architecture, 2022: `the-c4-model-for-visualising-software-architecture-2022.pdf`
- arc42
  - Website: <https://arc42.org/>
  - Docs (tips): <https://docs.arc42.org/home/>
  - Examples: <https://examples.arc42.org/>
  - FAQ: <https://faq.arc42.org/home/>
  - Template: <https://github.com/arc42/arc42-template>
  - Books:
    - arc42 in Aktion, 3rd edition, 2026: <https://www.hanser-fachbuch.de/arc42-in-Aktion/978-3-446-48491-7>
    - arc42 by Example, 3rd edition, 2023: <https://leanpub.com/arc42byexample>
    - Softwarearchitekturen pragmatisch dokumentieren (arc42 Primer), 3rd edition, 2023: `softwarearchitekturen-pragmatisch-dokumentieren-3th-edition-2023.pdf`
- Software guidebook
  - The software guidebook, 2022: `the-software-guidebook-a-guide-to-documenting-your-software-architecture-2022.pdf`
  - Excerpt (sections 3-15) of: <https://raw.githubusercontent.com/weibeld/assets/main/the-software-guidebook-simon-brown.md>
- Patterns 42 (might be obsolete - last update in 2024)
  - Website: <https://patterns.arc42.org/home/>
  - GitHub: <https://github.com/arc42/patterns.arc42.org-site>

> Note: the base path for all PDF files is `Google Drive/books`.

* * *

## Insights

Insights gained from applying the Tableflipper workflow in practice on the test projects during the development phase.

### Always bundle external reference material instead of linking to it

During the weibeld/lithuanian-bakery project, the URLs of the ADR templates on <https://github.com/architecture-decision-record/architecture-decision-record> changed from one day to the other on 2026-10-07 (`locales/en/` was renamed to `locales/en-001/`) breaking all hardcoded links. So, relying on URLs for crucial information should be at best completely avoided.

### Specific points that should be backed with reference material

During the weibeld/lithuanian-bakery project, it was discovered that the following aspects lead to unsatisfactory results if they are not covered by reference material that the agent reads:

- Distinction between constraints and quality requirements: agent seemingly randomly categorises items as constraints rather than quality requirements
- Specification format of quality requirements: agent tends to make quality requirements verbose and sprawl in uneven ways instead of tightly organise and compound them
