---
classes: 
    - wide
    - dark-theme
title: "Building an Automated HelloFresh Menu Analytics Pipeline"
date: 2026-02-11
categories :
    - blog
tags: [data-engineering, etl]
# toc: true
# toc_label: "Table of Contents"
excerpt: "Designing a small, reproducible ETL pipeline and automated analytics dashboard using the HelloFresh API"
header:
#   overlay_image: /assets/images/innovation-sad.png
  overlay_filter: 0.5 # same as adding an opacity of 0.5 to a black background
#   caption: "Random picture"
---
## Building an Automated HelloFresh Menu Analytics Pipeline

### What the Project Does

Recently, I have been working on this [project](https://github.com/rhyslwells/Hellofresh-Menu-Analytics/tree/main) with the aim of building a small, automated analytics workflow around HelloFresh menu data.

I wanted a small, repeatable dataset that updated weekly. This was possible using the free HelloFresh API. Each week, menu and recipe information are pulled from the API and stored in a SQLite database. I designed the ETL workflow to be reproducible and easy to rerun from scratch.

A set of SQL queries analyses recent menu changes and generates summary insights. These outputs feed into an analytical dashboard that highlights features in the latest data. The dashboard is automatically published to [GitHub Pages](https://rhyslwells.github.io/Hellofresh-Menu-Analytics/) on a scheduled basis.

I initially explored Databricks as an execution environment. However, within the constraints of the free tier, API access and orchestration were limited. For a project of this scale, GitHub Actions offered a simpler and more transparent way to schedule the pipeline and publish results.

---

### What I Explored While Building It

The main goal of this project was to create an environment for experimenting with tooling, architecture, and repository structure.

* **ETL design using a Medallion structure:**
  Data is organised into Bronze and Silver layers, separating raw API ingestion from cleaned, query-ready tables. Using a Medallion structure in a project of this size may appear excessive. However, enforcing a separation between ingestion and transformation kept individual scripts shorter and more focused. It reduced the risk of accumulating too much logic in a single file and made experimentation easier. SQL queries were used both for exploration and to determine which transformations should be materialised into a Gold layer.

* **Automation with GitHub Actions:**
  GitHub Actions proved sufficient for low-volume orchestration of ingestion, transformation, analytics, and publishing. It kept scheduling logic version-controlled and close to the repository without introducing additional infrastructure.

* **Secure configuration management:**
  The HelloFresh API key is managed through GitHub Secrets and injected at runtime, ensuring credentials are not exposed in the codebase.

* **Copilot-assisted development:**
  GitHub Copilot in VS Code was used to translate well-defined GitHub issues into implementation steps. Writing detailed issues clarified intent and improved traceability between planned work and code changes. Maintaining repository `notes` helped capture design decisions and reference material, which could be linked directly from issues and pull requests.

* **Documentation as structural guidance:**
  A blueprint document in the repository outlines the layout and overall workflow, alongside documentation cataloguing significant changes. This made architectural decisions explicit and was helpful for AI-assisted development. It also helped ensure consistency as the project grew and features were added.

* **Schema reference with Mermaid:**
  A Mermaid diagram documents the SQLite schema and table relationships. Rendering the diagram directly in GitHub keeps it accessible during analysis without requiring external tools.

---

### What I Learned

Even though the analytical output has limited practical utility, the project functioned effectively as an environment for refining workflow and design decisions.

**Technical**
SQLite is sufficient for small analytical workflows when schema discipline is maintained and transformations are clearly separated.

**Architectural**
Even small projects benefit from explicit layering and documentation. Introducing structure early reduces ambiguity as complexity increases.

**Tooling**
GitHub Actions is often adequate for orchestrating low-volume pipelines. Keeping automation close to the repository simplifies maintenance.

**Deployment**
Static HTML dashboards are straightforward to publish but limit interactivity. Application frameworks such as Dash are likely more appropriate when faster iteration and richer user interaction are required.

This project showed how I want to structure small data pipelines: layered storage, automated execution, version-controlled documentation, and explicit schema design.

The next step is to extend this approach toward a more interactive, application-style dashboard. I plan to explore this in a follow-up project:
[https://github.com/rhyslwells/Dash](https://github.com/rhyslwells/Dash)
