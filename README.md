## Instruqt Skeleton

This repository contains a set of GitHub Actions workflows to manage the development of your Instruqt tracks. 

[Click here for the full documentation on building tracks with this developer workflow.](https://docs.instruqt.com/how-to-guides/build-tracks/maintain-a-developer-workflow#developer-workflow)

## Developer Workflow
From the repository that contains your Instruqt tracks:
1. Create a new branch by selecting **Main > View all branches > New branch.**
2. Select **Actions** from the top menu of your repository. On the left side, select the `convert` workflow. On the right side, expand the **Run workflow** dropdown menu, and select your new branch name. Next, provide the slug of the track you intend to modify. Finally, select **Run workflow**.
3. Go to your organization's [Instruqt page](https://play.instruqt.com/) and modify the development version of your track until you are satisfied with the changes.
4. Once the development version of your track is ready, return to GitHub and run the `promote` workflow from the **Actions** menu. Provide the same branch and track slug you used in the `convert` workflow.
5. Create a pull request by selecting **Pull requests** in the top menu of your repository, followed by **New pull request**. Indicate your new branch, and select **Create pull request**. 
6. Have a colleague review your work, and merge the pull request! Once merged, the changes will be applied to the production version of your track.
