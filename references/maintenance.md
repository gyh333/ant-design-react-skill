# Maintenance

Use this file when updating or publishing the skill.

## Release Criteria

- `SKILL.md` frontmatter name matches folder name.
- `SKILL.md` references only existing files.
- README structure matches actual folders.
- `metadata.json` version and license are accurate.
- Examples contain no private endpoints, secrets, company data, or proprietary business rules.
- Version-sensitive APIs are framed as "verify installed package or official docs" instead of hard guarantees.

## Adding Examples

When adding a component or workflow example:

- Keep it focused on one concept.
- Include production notes.
- Prefer TypeScript.
- Avoid introducing new project dependencies unless the example is explicitly about that integration.
- Update `references/component-index.md`.
- Update README structure or content scope if the new category is user-visible.

