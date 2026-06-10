# 06 - Open Items And Risks

## Documentation Gaps

- A single end-to-end public onboarding guide exists in pieces, but not as one polished external manual.
- The "one command" client provisioning system is not complete.
- Some source docs still contain internal IDs, local paths, private account references, or credential pointers.
- Raw operating memory is useful internally but should not be pushed to a public repository.

## Product/Runtime Risks

- Some accounts may still have cloud and self-hosted duplicate workflows.
- A GHL webhook value pointing to the wrong runtime can silently break a product.
- A copied snapshot can preserve stale product logic if the source is not audited first.
- Visual GHL workflow bump/reminder conditions are harder to verify than n8n workflow nodes.
- Product-level QA must be run per client and per channel before disabling old workflows.

## Website/UI Boundary

- Website/demo-page changes are separate from this handoff package.
- The internal Crowdsnare all-options test page and the LAR English/French duplicate should stay separate.
- Exact domain ownership/access can block restoring a specific public URL even when local files are correct.

## Handoff Risks

- Pushing raw repo state without sanitization would leak private operational details.
- Publishing `.env`, client exports, screenshots, OAuth details, or raw message logs is unsafe.
- Some local docs are written for an internal operator and should be rewritten before public use.

## Recommended Next Steps

1. Decide whether this GitHub repository is private or public.
2. If public, run a full secret scan before push.
3. Keep this handoff folder as the public-safe docs surface.
4. Move deeper implementation docs into private docs or scrub them first.
5. Build a deterministic provisioning CLI around the current onboarding/migration scripts.
6. Finish the LAR/ReVAI demo page polish separately from documentation.
