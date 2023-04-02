## Instruqt Skeleton
[![Instruqt Validate, Push, and Test](https://github.com/instruqt/skeleton/actions/workflows/test-prod-tracks.yml/badge.svg)](https://github.com/instruqt/skeleton/actions/workflows/test-prod-tracks.yml)

This repository contains a set of GitHub Actions workflows to manage the development of your Instruqt tracks. 

[Click here for the full documentation on building tracks with this developer workflow.](https://docs.instruqt.com/how-to-guides/build-tracks/maintain-a-developer-workflow#developer-workflow)

## Developer Workflow
From the repository that contains your Instruqt tracks:
1. Create a new branch by selecting **Main > View all branches > New branch.**
2. Select **Actions** from the top menu of your repository. On the left side, select the `copy-prod-track-to-dev` workflow. On the right side, expand the **Run workflow** dropdown menu, and select your new branch name. Next, provide the slug of the track you intend to modify. Finally, select **Run workflow**. You must run this workflow on your dev branch, and not on the main/master branch which is not allowed for safety purposes. Also note that if you already have a dev version of this track it will be overwritten with the prod version to provide a clean starting environment.
3. Go to your organization's [Instruqt page](https://play.instruqt.com/) and modify the development version of your track until you are satisfied with the changes. Test your track in the UI until you are happy with its performance. When your track is working smoothly and all check/solve scripts are functional, turn off maintenance mode. You must disable maintenance mode on the dev track to proceed!
4. Once the development version of your track is ready, return to GitHub and run the `prepare-dev-for-pull-request` workflow from the **Actions** menu. Provide the same branch and track slug you used in the `copy-prod-track-to-dev` workflow.
5. Create a pull request by selecting **Pull requests** in the top menu of your repository, followed by **New pull request**. Indicate your new branch, and select **Create pull request**. 
6. Have a colleague review your work, make sure the tests all pass, and merge the pull request! Once merged, the changes will be applied to the production version of your track and production will receive another round of post-merge testing. You can review the results of the tests in the Actions tab of your repo.

## Tips
This workflow is designed to use a single track per branch for development. If you need to work on multiple tracks create separate branches and dev copies for each track.

Do not forget to run the `prepare-dev-for-pull-request` workflow before creating your pull request. You'll know you've made this mistake if you see DEV code in the changes page of the pull request. As always, carefully review ALL your changes before merging a PR to ensure you don't wreck your production environment.

You can test your production tracks any time by manually running the test-prod-tracks workflow from the Actions tab. You can also schedule nightly or weekly tests of your production tracks by adding a `schedule` block to the `on:` trigger section of the test-prod-tracks YAML:

```
  schedule:
    # * is a special character in YAML so you have to quote this string
    # This runs weekly on Sunday at 5:00 am
    - cron:  '0 5 * * 0'
```

You can put a status badge on your README.md by changing the URL in this template to match your own repo. It will show the status of the last test-prod-tracks run.

For extra protection you can turn on Github branch protection for your main/master branch, and require a coworker to review changes before a merge. This is strongly recommended!
