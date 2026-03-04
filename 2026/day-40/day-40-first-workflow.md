### Task 3: Understand the Anatomy
Look at your workflow file and write in your notes what each key does:
- `on:`- Defines what event starts the workflow. It runs with every push
- `jobs:`- A workflow can have multiple jobs and each jobs have separate runner
- `runs-on:`- Specifies which machine runs the job.
             ubuntu-latest = GitHub provides a Linux VM.
- `steps:`- each job have steps which contains list of actions executed in order  inside the job.
- `uses:` -Used when you want to use a prebuilt action.
Example: actions/checkout pulls your code.
- `run:` -Executes shell commands directly on the runner.
- `name:` (inside the step) Just a label shown in the UI to make it readable.

Task 5: 

When I added and pushed name and run in step for intetional error exit code 1 and exit code 127. I observed-
-Red cross
-Workflow marked as failed
-The failing is step highlighted.
-I saw below error when clicked on failed step -
  Process completed with exit code 1.
-Then I removed that step and added fix step, pushed it to github and then observed the run it was green as I added fix step removing failed.