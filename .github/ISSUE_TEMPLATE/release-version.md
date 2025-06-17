---
name: Release new version
about: Plan and subtasks for releasing a new version
title: "[rel] Release vX.Y.Z"
labels: ''
assignees: ''

---

based on [Edirom-Online Release Workflow](https://github.com/Edirom/Edirom-Online/blob/develop/docs/release-workflow.md) with changes for API

Preparations on [zenodo.org](https://zenodo.org)
- [ ] go to previous version and click "New version"
- [ ] reserve a DOI -> *insert here*
- [ ] update version and other metadata in publication form
- [ ] upload a placeholder file
- [ ] save draft -> *link here*

Checkout develop branch: `git checkout develop`
- [ ] have a look into release milestone and manage last issues and PRs

Checkout new release branch: `git checkout -b release/vX.Y.Z develop`
- [ ] update CITATION.cff (date, contributors, version, DOI)
- [ ] bump version number everywhere (find/replace in code), e.g. in swagger.yml
- [ ] commit version release branch

Checkout main branch: `git checkout main`
- [ ] `git merge --no-ff release/vX.Y.Z` (release branch into main)
- [ ] (potentially) resolve merge conflicts and `git continue merge`
- [ ] `git tag` returns a list of all tags
- [ ] `git tag -a vX.Y.Z -m "vX.Y.Z"`
- [ ] (potentially) `git tag` for review
- [ ] `git push --follow-tags`

Release on [github.com](https://github.com) 
- [ ] Go to tag vX.Y.Z and click "Release from Tag"
- [ ] auto-generate the release description
- [ ] publish the release on GitHub - *link GitHub release*

Checkout develop branch: `git checkout develop`
- [ ] `git merge --no-ff release/vX.Y.Z` (release branch into develop)

Publication on [zenodo.org](https://zenodo.org)
- [ ] edit publication draft
- [ ] remove placeholder file and upload files copied from *GitHub release*
- [ ] double-check metadata
- [ ] publish on Zenodo (with updated files) -> *link publication DOI*

Clean-up
- [ ] delete branch *release/vX.Y.Z*
- [ ] announce new version to Edirom-Online community
