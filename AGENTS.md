# Component library working guide

## This repository: shopify-themes
Part of the Goodform Shopify Library (GitHub organization `goodformco`):

- `shopify-foundations`: small, single-purpose elements, such as
  cart products, cart summary, clear all, empty cart, suggestion
  row, drawer swipe, menu drawer.
- `shopify-components`: complete components composed of
  foundations, such as a cart drawer or a header.
- `shopify-themes` (this repo): finished themes composed of
  components.

Rules for this level:
- A theme holds no copied component or foundation code. It lists
  the base theme and version, the components it uses (each with
  its release tag), any foundations used directly, and the order
  to install them.
- A theme keeps only what belongs to that theme: its settings,
  template and layout choices, theme-level integration, and its
  own test evidence.
- To fix a component or foundation, change it in its own
  repository and release a new version there; then update the
  version listed here.
- Release each theme with its own tag:
  `<theme>-v<MAJOR.MINOR.PATCH>`.


## Purpose
Build a reusable theme component library incrementally.
Preserve proven work, document dependencies, and improve it
when a real project needs it.

Do not turn extraction into an automatic redesign.

## Working with the owner
- The owner makes repository and theme edits unless they
  explicitly delegate them.
- Give small, sequential steps.
- For existing code, provide exact find-and-replace instructions.
- Read current files before suggesting corrections.
- When asked to check work, inspect the saved version.
- Do not claim a change is saved or verified without evidence.
- Keep live themes untouched. Test in an unpublished theme.
- Do not resume parked work without a new brief.

## Start each round with a scope
Identify:
- The intended use.
- The source of truth.
- What this round will deliver.
- What remains outside scope.
- The checks required to finish.

Preservation, installation testing, standalone portability,
and new features can be separate rounds.

## Preserve before improving
- Preserve working source without unnecessary changes.
- Keep independently useful modifications separate.
- Do not quietly bundle unrelated features.
- Preserve existing settings and flexible content structures.
- Distinguish component-owned controls from controls supplied
  by child blocks or the destination theme.
- Do not replace flexible child blocks with fixed fields
  merely to simplify extraction.

## Dependency inspection
Trace:
- Child blocks and rendered snippets.
- Referenced assets and nested dependencies.
- Theme classes, CSS variables and global settings.
- Editor and storefront translations.
- Saved layout, content and resource references.

Matching filenames alone do not establish compatibility.
State what files or versions were actually compared.

Do not copy entire theme systems when a component only
needs a small part of them.

## Repository organization
Use a descriptive component directory.

Typical structure:

component-name/
  README.md
  DEPENDENCIES.md
  INSTALL.md
  files/
    blocks/
    sections/
    snippets/
    assets/
  translations/
  examples/

Create only the directories and documents needed.

- files/ mirrors paths in the destination theme.
- translations/ holds entries to merge, not whole replacement
  locale files unless explicitly intended.
- examples/ holds optional saved layouts or sample content.
- Never present an entire homepage replacement as a normal
  component installation step.
- Small components may keep installation instructions in
  README.md instead of a separate INSTALL.md.

## Documentation
Start every component README with a `## Brief` section directly
under the title: a one-sentence definition, then What it does,
Settings, Scope, Files, Built for, and Evidence (tested,
owner-confirmed, untested). Keep it short; details go below.

Explain:
- What the component does.
- Its structure and independent settings.
- Its current dependency and portability status.
- How to install it without overwriting unrelated work.
- What must be configured separately.
- What was tested, where, and when.
- Known limitations and deferred improvements.

Keep documentation proportional.
Write or finalize the README after testing when practical.
Keep earlier status statements consistent with later results.

## Installation and testing
- Use an unpublished compatible theme.
- Compare files before overwriting anything.
- Merge missing translation entries without duplicate keys.
- Preserve unrelated settings, files and translations.
- Run Theme Check and distinguish new issues from existing ones.
- Test the component's intended behavior and core controls.
- Check desktop and mobile layouts.
- For interactive components, check keyboard operation and
  visible focus.
- Check multiple instances when relevant.
- Record anything not tested.

Editor mobile preview is not physical-device testing.
One successful theme installation is not cross-theme validation.
A clean lint result is not proof of visual or functional success.

## Evidence and status
Distinguish:
- Source preserved.
- Dependencies inspected.
- Installed in a named test theme.
- Specific interactions or settings tested.
- Broader validation not performed.

Label owner-reported results as owner-confirmed.
Do not claim every setting passed from a general report
that the component works.

An optional behavior that was never implemented is not
automatically a defect or a failed test.

## Future component design
When a round specifically addresses customization:
- Let each reusable feature own its settings.
- Default to sensible theme inheritance where practical.
- Offer independent overrides progressively.
- Keep routine setup simple.
- Keep theme-specific mappings in a small integration layer.
- Add settings for real needs, not every imaginable option.

These principles do not authorize redesign during extraction.
Avoiding unnecessary theme dependencies is more useful than
avoiding Liquid for its own sake.

## Stopping rule
Park a component when:
- Its agreed intended use works.
- Installation is documented and repeatable within its scope.
- Core checks for that round pass.
- Limitations are recorded.

Only issues blocking the agreed use keep the round open.
Optional improvements go to the backlog, not automatic
scope expansion.

Reopen for a real project need, a meaningful reported problem,
or a recurring limitation that causes work.

Do not polish one component indefinitely.
A theme-dependent baseline can be a completed round;
standalone portability can wait.

## Handoff
Before starting work, another agent should read:
1. This guide.
2. The relevant component's current documentation.
3. The actual source files involved.

Follow the owner's latest instructions.
If direct repository access is unavailable, provide precise
manual edits rather than implying a commit was made.
