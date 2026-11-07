# Repository AI development rules

## Mandatory cross-project implementation protocol — owner directive, 2026-11-07

This contract applies to **every feature, fix, UI update, data migration, and AI-assisted development session**. It supplements (never weakens) stricter project-specific rules above or in other docs.

1. **Preserve the original working implementation.** At session start, review the actual current repository, approved UI, design system, architecture, open PRs, test evidence, screenshots, and latest project handoff. Identify the known-good baseline. Never replace a functioning app or UI with a disconnected rebuild because a new architecture or role separation is requested.
2. **Branch first.** Create a separate feature/fix branch based on the verified original code / current main. Commit all implementation only to that branch. No direct implementation changes to `main`, no forced pushes, and no destructive migration.
3. **One scoped PR per implementation.** Open a PR targeting `main` with problem statement, affected files/features, behavior contracts, backwards compatibility, security/privacy risks, screenshot references, and test plan. Do not combine unrelated tasks or silently change product scope.
4. **Integration, not replacement.** Trace dependencies and existing flows before editing. Layer changes onto existing components, routes, state, APIs, database and layouts. Preserve customer data, branding, typography, interactions, navigation, assets, and already-working behavior unless the owner expressly approves a change.
5. **Preview before merge.** Publish a distinct Cloudflare Pages (or the app's existing platform) preview for the PR. Keep production/current main unchanged while testing. Verify the preview is actually running the PR commit, not a stale site or local-only screenshot.
6. **Regression and real-use testing.** Run typecheck/lint/unit/integration/build plus actual user-path tests relevant to changes (desktop/mobile UI, login, role switching, location, payment, offline/sync, permissions, etc.). Compare approved baseline versus PR preview. Explicitly record what passed, failed, or could not be tested.
7. **Review and approval gate.** **Do not merge until the owner can review the PR preview and the change demonstrably works with the existing application.** A green build, deployed URL, or AI claim of completion is not authorization to merge. Maintain rollback path.
8. **Security and data boundaries.** New UI cannot grant privileges. Enforce roles, RLS/tenant ownership, order state, location privacy, payment rights, and audit on the server. Never publish credentials or customer data, use fake proof, or promise security without testing.
9. **Durable handoff.** At each session end, update the project's state/handoff with current branch/PR/preview, what was implemented, verified versus unverified, pending decisions, tests, blockers, rejected approaches, regression risks and exact next step. The next agent must read this before coding.
10. **When source appears missing, investigate first.** Search earlier conversation artifacts, Git history, deployments/versions, file library, and existing projects. Do not tell the owner to recreate or upload code without checking these sources. If source is genuinely unrecoverable, say precisely what was checked and keep any visual reconstruction strictly on a review PR.

This is a universal owner preference. Do not treat each new chat or AI agent as authorization to ignore it.
