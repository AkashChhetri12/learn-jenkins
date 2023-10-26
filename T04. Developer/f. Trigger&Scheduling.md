# Triggers and Scheduling in Jenkins

In Jenkins, triggers and scheduling are essential concepts that allow you to control when and how your jobs or pipelines are executed. Jenkins provides various ways to trigger and schedule jobs based on different events, time intervals, or external triggers.

1. **Manual Execution:**
   - **User Initiated:** Jobs can be executed manually by users through the Jenkins web interface. This is the simplest form of job execution and is initiated when a user clicks the "Build Now" or "Build" button for a specific job.

2. **SCM Triggers:**
   - **Polling SCM:** Jenkins can automatically trigger jobs when changes are detected in a version control system (e.g., Git, SVN). You can set up polling intervals to check for changes and trigger jobs when new commits are found. This is configured in the job's "Build Triggers" section.

3. **Webhooks and Hooks:**
   - **Webhooks:** Jenkins can listen for incoming webhooks from your version control system, and other external systems, and trigger jobs based on these events. This provides real-time triggering when changes occur.
   - **GitHub Hooks:** For GitHub repositories, you can use GitHub webhooks to trigger Jenkins jobs upon specific events, such as code pushes or pull requests.

4. **Timer-Based Scheduling:**
   - **Build Periodically:** You can schedule jobs to run at specific time intervals using cron-like syntax. This is configured in the job's "Build Triggers" section. For example, to schedule a job to run every day at midnight:

     ```
     H 0 * * *
     ```

   - **Pipeline DSL (`cron`):** In scripted and declarative pipelines, you can use the `cron` trigger to schedule pipeline runs.

     ```groovy
     triggers {
         cron('H 0 * * *')
     }
     ```

5. **Upstream/Downstream Projects:**
   - Jobs can be triggered based on the success or failure of other jobs. For example, you can configure a downstream job to trigger only if its upstream job succeeds. This is defined in the job's configuration.

6. **Parameterized Builds:**
   - Jenkins allows you to trigger parameterized builds where you can specify parameters at the time of triggering the build. Parameters can be passed via the web interface, API, or other triggering mechanisms.

7. **Remote Execution and APIs:**
   - Jenkins provides a REST API that allows external systems to trigger jobs programmatically. This is useful for integrating Jenkins with other tools or building custom triggering mechanisms.

8. **Pipeline DSL (`input`):**
   - In scripted and declarative pipelines, you can use the `input` step to introduce manual approval steps. This means a job won't proceed until an authorized user approves it.

   ```groovy
   input('Proceed with deployment?')
   ```

9. **GitHub Pull Request Builder Plugin:**
   - If you're working with GitHub pull requests, you can use the GitHub Pull Request Builder plugin to automatically trigger builds on pull request events.

10. **Jenkinsfile Triggers:**
    - In multibranch pipelines, Jenkins can detect and trigger jobs based on the presence of a `Jenkinsfile` in a branch. When a new branch with a `Jenkinsfile` is detected, a corresponding job is created.

