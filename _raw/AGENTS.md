# Wiki authoring rules

## Workspace and structure

- Update this knowledge base through the `llmwiki-cmalek-languages` MCP server.
- Treat raw sources as evidence and write curated material only under `/wiki/`.
- Keep `/wiki/overview.md` and `/wiki/source-map.md` useful as the entry points whenever a new topic or relationship is added.

## Sources and links

- Every factual claim needs a Markdown footnote that links directly to the actual cited source article.
- Use vault-root-relative Markdown links, never localhost URLs: `[^1]: [Christianity in Anglo-Saxon England](Old%20English/History/Christianity%20in%20Anglo-Saxon%20England.md)`.
- Link text should be a readable article title, without a bare filename or extension. The root-relative target path supplies the source context.
- The LLM Wiki linter may report these valid vault-source links as dangling because raw sources are not compiled wiki pages. Do not replace them with localhost URLs to silence that false positive.
- Whenever prose names a source file, make that filename a direct link to the source instead of plain text.
- Prefer contextual page links over raw filenames for compiled wiki pages.

## Old English

- Organize Old English material as a connected system: language, texts, people, places, institutions, and material things (such as writing systems and objects) should link to one another when the sources support the relationship.
- For texts, connect linguistic details to their speakers, named people, geographic setting, social institutions, and material vocabulary rather than treating the text as isolated content.

## Quality bar

- Give every page required frontmatter, at least one useful visual element, and meaningful cross-links.
- Run the MCP wiki linter after changes. Fix genuine errors; report the known raw-source-link false positives and other warnings honestly.
