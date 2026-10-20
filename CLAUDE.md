# cmalek-linguistics vault

## Wiki environment check

The wiki environment is set per shell by `select-wiki` (`~/.profile.d/obsidian-wiki.sh`). At the start of any wiki skill run (ingest, lint, capture, research), confirm before writing:

- `$OBSIDIAN_VAULT_PATH` is `/Users/cmalek/Documents/vaults/cmalek-linguistics`
- `$QMD_WIKI_COLLECTION` is `cmalek-linguistics`

If either differs, stop and tell the user to run `language-wiki` in their shell. Do not override the variables inline.

## QMD refresh

After any skill writes vault markdown, run `qmd update`, then `qmd embed` if it reports vectors are needed, then verify a changed page with `qmd ls cmalek-linguistics`. `qmd update` indexes every collection, so verify against this vault's collection, not the first one listed. Do not skip this step; check the variable's value rather than assuming it is unset.
