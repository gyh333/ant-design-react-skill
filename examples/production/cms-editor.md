# CMS Editor

Use this pattern when Ant Design forms wrap a rich text editor.

Recommended fields:

- Title
- Slug or route path
- Category
- Tags
- Cover image
- Rich text body
- SEO summary
- Publish status and schedule time

Production checks:

- Separate draft save from publish.
- Sanitize HTML on the server.
- Validate uploaded images on both client and server.
- Warn before leaving with unsaved changes.
- Preview content in a safe rendering environment.
- Keep editor integration isolated behind a local wrapper component.

Do not introduce a rich text editor dependency unless the project already uses one or the user asks for it.

