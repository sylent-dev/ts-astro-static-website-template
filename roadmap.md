# Roadmap

The steps chosen for the site described in [specs.md](specs.md), following [process.md](process.md). Each step is delivered in its own pull request, which checks its box. What is noted and not chosen yet lives in [backlog.md](backlog.md).

## Size of the project

<!-- Chosen with the owner at the setup (process.md, Size the project): the tools this project uses, and how far. For example: « A brand site of a few page types: every tool, in order, for the first cycle. » -->

## Reference

Read only by the steps that need them:

- [Technical choices](docs/technical-choices.md): the stack, the commands and the main designs, with their reasons.
- [Branding](docs/branding.md): the brand assets, the visual identity and every design decision of the mock-up, with the tokens.
- [External services](docs/external-services.md): limits and terms of the services, and the risks accepted by the owner.
- [Lessons](docs/lessons.md): what working on the project taught, kept for the retrospectives.
- [Roadmap archive](docs/roadmap-archive.md): the detail of the steps done, moved there once their pull request is merged.
- [Backlog](backlog.md): what is noted and not chosen yet, read when the next work is chosen.

## Models

Each step to come names the Claude model recommended for its session, so that the owner switches with `/model` before starting it; a new step or sub-step gets its model when it is written here. A judgment of what a quiet mistake would cost, not of the size of the step: Fable 5.2 for critical code (the rules of an external service the site must not break, what a form sends and to whom, the data a page states as true); Opus 5.5 for every other step (specifications, mock-up, pages, refactoring, launch, documentation).

The subagents (`code-reviewer`, `dependency-reviewer`) name no model and run on the model of the session, but a code review, whose model follows what it reads: Opus 5.5 for a pull request of tests alone or of moves alone; Fable 5.2 for critical code; the model of the session otherwise. Claude Code gives `code-reviewer` its model when it launches it, and says it with the cost of the review; the notes of a review name at their top the model that wrote them. If a step proves harder than its model (a review that keeps finding medium recommendations, a design that doesn't settle), say so and propose to switch.

## Steps

<!--
The usual steps of the first cycle of a site; adapt them at the setup, one line per step done with its pull requests. Each step names its model and the tools it needs (process.md, Size a change). A later cycle adds its steps under a heading of its own (« Cycle 2: testimonials and an English version »), numbered after the last one.
-->

### Cycle 1: the site online

- [ ] **0. Project setup** (model: Opus 5.5): the size of the project, the Project section of `CLAUDE.md`, the name of the site, the port of the mock-up server, the repository settings.
- [ ] **1. Specifications and structure** (model: Opus 5.5): audiences, value proposition, brand assets, external services; the content tree in Excalidraw, the URLs and redirects.
- [ ] **2. Wireframes** (model: Opus 5.5): one Excalidraw wireframe per page type, phone first.
- [ ] **3. Mock-up** (model: Opus 5.5): 3 or 4 styles, then every page of the first release in `docs/mockups/`, checked on the owner's phone; decisions in `docs/branding.md`.
- [ ] **4. Design system** (model: Opus 5.5): the tokens in `docs/branding.md`, the mock-up rewritten to use only them, an entry in `design-journal.md`.
- [ ] **5. Skeleton and deployment** (model: Opus 5.5): the tokens and fonts of the mock-up in `src/styles/`, the brand assets (`npm run brand:images`), the header and footer, the deployment to the `github.io` preview.
- [ ] **6. Pages** (model: Opus 5.5): one step per page type, as specified.
- [ ] **7. Quality review** (model: Opus 5.5, Fable 5.2 for the critical areas): before the launch, the whole site reviewed area by area (process.md, Launch): `code-reviewer` in its area mode, one pass per area at once (the layouts and components, the pages, the styles, the scripts and the build), each told what the others read and given the results of `npm run check` run once before them, against SOLID, DRY and KISS. Its findings split into pull requests: the fixes of behavior, what needs a mock-up, the moves last.
- [ ] **8. Launch** (model: Opus 5.5): the site checked on the preview, the DNS switched by the owner, the custom domain and HTTPS.
- [ ] **9. First retrospective** (model: Opus 5.5): right after the launch, while the lessons are fresh: the lessons of `docs/lessons.md` sorted one by one with the owner (process.md, Retrospective), into this project, the templates, or dropped; the backlog sorted, the memory moved to the files.

### After the launch

- [ ] **Polish** (model: Opus 5.5): the last touches, picked with the owner from `backlog.md`.
- [ ] **Second retrospective** (model: Opus 5.5): right after the polish, the same sorting on the lessons written since the first one, with the visitors' feedback as well.

The steps may be split into sub-steps when a pull request grows too large. When no step is left, Claude Code proposes the next items of the backlog to the owner.
