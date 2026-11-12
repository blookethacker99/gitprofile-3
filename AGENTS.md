# AGENTS.md

Guidance for AI coding agents working in this repository.

## What this project is

GitProfile is a **fork-first portfolio template**. It builds a portfolio site from a GitHub username: the profile, avatar, bio and repositories are fetched from the public GitHub API at runtime, so there is no database and no backend.

Most people arrive here by forking the repo and deploying it to GitHub Pages. Assume that is the task unless told otherwise.

## Customizing a portfolio: edit one file

**`gitprofile.config.ts` is the only file that needs to change to customize a portfolio.** Do not edit anything under `src/` to change someone's name, links, jobs, skills or projects — every one of those is a config value.

`github.username` is the only required option. Every other section can be left empty or as an empty array, which hides that section from the rendered page.

### The `base` option is the most common source of breakage

`base` must match the deployment target, or the site builds fine and then loads without CSS or JavaScript:

- Deploying to `https://<USERNAME>.github.io` → `base: '/'`
- Deploying to `https://<USERNAME>.github.io/<REPO_NAME>` → `base: '/<REPO_NAME>/'` (leading and trailing slash)
- Deploying to Vercel, Netlify or a custom domain → `base: '/'`

It is read by `vite.config.ts`, not by the React app, so a change to it only takes effect on rebuild. Note that `base` is deliberately absent from the `SanitizedConfig` interface for this reason.

## Layout

| Path                                  | What lives there                                                 |
| ------------------------------------- | ---------------------------------------------------------------- |
