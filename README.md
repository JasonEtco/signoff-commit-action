<h3 align="center">[WIP] signoff-commit-action</h3>
<p align="center">A GitHub Action that creates an empty commit with a list of commits to "sign off on".</p>

| ![Screenshot](https://user-images.githubusercontent.com/10660468/70858898-9c2a2b80-1ed8-11ea-9ee8-172b7e434a2d.png) |
| --- |

> **Note**: This is super WIP - at the moment, it uses [actions/github-script](https://github.com/actions/github-script) to spike out functionality [directly in the workflow file](/.github/workflows/signoff.yml). This will eventually be moved to a reusable action instead.

---

Current limitations:

* Obviously, this is written directly into the YAML file. We'd move it out to a JS Action.
* This runs an Actions workflow on every issue comment - _every_ issue comment. Might be able to lift some of that to the workflow (via [`steps[].if`](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/workflow-syntax-for-github-actions#jobsjob_idstepsif)) but this could cause usage/billing problems.
* The commit is shown as being authored and committed by GitHub Actions; we can't easily say "authored by <user>" because that requires an email that we don't necessarily have. We can try to get the user's public email, or from a previous commit.
