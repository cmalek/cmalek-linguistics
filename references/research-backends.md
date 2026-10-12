# Optional CLI backends for wiki-research. Delete rows you don't need.
# Skill docs: .skills/wiki-research/SKILL.md — Research Backends section
backends:
  # --- free / local ---
  - name: defuddle-fetch
    binary: defuddle
    invoke: "defuddle '{url}'"
    when_to_use: any URL — cleaner extraction than WebFetch alone
    cost_tier: free
    env_key: ""
    output: markdown

  - name: yt-dlp-transcript
    binary: yt-dlp
    invoke: "yt-dlp --skip-download --write-auto-sub --sub-lang en --sub-format json3 -o /tmp/ytvid '{url}'"
    when_to_use: YouTube video URLs for transcript extraction
    cost_tier: free
    env_key: ""
    output: text

  # --- paid / gated (skipped when env key is unset) ---
  - name: perplexity-sonar
    binary: perplexity
    invoke: "perplexity search '{query}'"
    when_to_use: deep synthesis queries needing multi-source aggregation
    cost_tier: paid
    env_key: PERPLEXITY_API_KEY
    output: text
