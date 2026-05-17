# CLAUDE.md — Zenith Digital MENA Project Rules

Standing rules for any Claude Code session working in this repo. Read this at the start of every session.

## Spec
The full project specification lives in `docs/REVAMP-BRIEF.md`. Read it before making non-trivial changes.

## Project state
- Active development branch: `revamp-foundation` (off `revamp`)
- `main` is production (currently the pre-revamp site)
- Phase 1 Steps 1–3 complete and deployed to the Cloudflare preview as of yesterday
- Deployment: Cloudflare Pages, auto-builds from any pushed branch

## Working rules

1. **Branch names use hyphens, not slashes.** `revamp-foundation`, not `revamp/foundation`. Git treats slashes as folder-like hierarchy and won't allow `revamp/foundation` alongside an existing `revamp` branch.

2. **Locked copy from the brief is verbatim.** If you think a line should change, propose the change as a question first. Do not rewrite unilaterally.

3. **Call bugs bugs.** Never frame broken behavior as "intentional for now" or "deferred work." If a behavior is broken in the current implementation, name it as a bug and let the user decide whether to fix or defer.

4. **Show complete file content as a code block before any write.** Diff displays in the terminal can be ambiguous; the user will scrutinize the full intended content before approving.

5. **For high-risk file modifications, use the create-new + cat verify + mv pattern.** This applies to `Layout.astro`, `Header.astro`, `Footer.astro`, and any other file where the diff renderer has previously shown ambiguous output. Write to `[file].new.[ext]`, cat to verify, then `mv` to overwrite.

6. **After each file write, cat the file and show the relevant section.** Don't trust the diff display alone — always confirm on-disk state.

7. **Commit attribution.** Include `Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>` on every commit, consistent with Steps 1–3.

## Locked design system tokens
The full design system lives in §2 of the brief. Critical locked values that must not drift:
- Colors: bg-primary `#050507`, bg-secondary `#0A0A0C`, bg-tertiary `#111114`, accent-primary `#6BA0D8`, accent-soft `#A8C5E0`, accent-deep `#1E4A78`
- Fonts: Geist (EN display), IBM Plex Sans Arabic (AR display), Geist Mono (mono). Self-hosted, woff2 only, subsetted.
- Weights: 400 and 500 only. No 600 or 700.

## Banned words (no exceptions, any locale)
transform, leverage, synergy, journey, ecosystem, holistic, partner with, unleash, empower, bespoke, tailored, world-class, cutting-edge, passionate, dedicated, drive results, take to the next level, push boundaries, reimagine, reinvent, robust, seamless, end-to-end, future-proof, dynamic, innovative, solutions (as in "digital solutions")

Use plain alternatives: build, work on, design, engineer, ship, deliver, run, help, lead, refuse, choose, decide.
