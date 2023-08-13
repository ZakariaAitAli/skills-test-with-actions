<header>

<!--
  <<< Author notes: Course header >>>
  Include a 1280×640 image, course title in sentence case, and a concise description in emphasis.
  In your repository settings: enable template repository, add your 1280×640 social image, auto delete head branches.
  Add your open source license, GitHub uses MIT license.
-->

# Test with Actions

_Create workflows that enable you to use Continuous Integration (CI) for your projects._

</header>

<!--
  <<< Author notes: Step 3 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
-->

## Step 3: Upload test reports

_The workflow has finished running! :sparkles:_

So what do we do when we need the work product of one job in another? We can use the built-in [artifact storage](https://docs.github.com/en/actions/advanced-guides/storing-workflow-data-as-artifacts) to save artifacts created from one job to be used in another job within the same workflow.

To upload artifacts to the artifact storage, we can use an action built by GitHub: [`actions/upload-artifacts`](https://github.com/actions/upload-artifact).

### :keyboard: Activity: Upload test reports

1. Edit your workflow file.
1. Add a step to your `build` job that uses the `upload-artifacts` action.

   ```yaml
   build:
     runs-on: ubuntu-latest
     steps:
       - uses: actions/checkout@v3

       - name: Run markdown lint
         run: |
           npm install remark-cli remark-preset-lint-consistent
           npx remark . --use remark-preset-lint-consistent --frail

       - uses: actions/upload-artifact@v3
         with:
           name: remark-lint-report
           path: public/
   ```

1. Commit your change to this branch.
1. Wait about 20 seconds then refresh this page (the one you're following instructions from). [GitHub Actions](https://docs.github.com/en/actions) will automatically update to the next step.

Similar to the upload action to send artifacts to the storage, you can use another action built by GitHub to download these previously uploaded artifacts from the `build` job: [`actions/download-artifact`](https://github.com/actions/download-artifact). To save you time, we'll skip that step for this course.

<footer>

<!--
  <<< Author notes: Footer >>>
  Add a link to get support, GitHub status page, code of conduct, license link.
-->

---

Get help: [Post in our discussion board](https://github.com/skills/.github/discussions) &bull; [Review the GitHub status page](https://www.githubstatus.com/)

&copy; 2023 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

</footer>
