# Jenkins terminology 

1. **Jenkins:**
   Jenkins refers to the automation server itself. It is the core software that facilitates automation, integration, and continuous delivery in a software development environment.

2. **Job:**
   A job in Jenkins represents a task or unit of work. It can be a build job, test job, deployment job, or any other task you want to automate. Jenkins jobs are the basic building blocks of automation.

3. **Build:**
   A build in Jenkins is the process of compiling, assembling, and packaging source code into executable artifacts. It's often a crucial step in the software development workflow.

4. **Freestyle Project:**
   A type of Jenkins job that allows you to configure tasks and build steps using a graphical user interface. It's suitable for simple automation tasks.

5. **Pipeline:**
   A Jenkins Pipeline is a way to define your automation as code. It allows you to define complex, multistage workflows for building, testing, and deploying code using a Domain Specific Language (DSL) known as Groovy.

6. **Node/Agent:**
   A node or agent is a machine (physical or virtual) that executes Jenkins jobs. Jenkins can distribute workloads across multiple nodes to perform builds and other tasks in parallel.

7. **Executor:**
   An executor is a computational resource on a node that can run Jenkins jobs. A single node can have multiple executors, enabling concurrent job execution.

8. **Master:**
   The Jenkins master is the main server where the Jenkins automation server is running. It manages job scheduling, agent coordination, and overall Jenkins configuration.

9. **Workspace:**
   The workspace is a directory on a node where Jenkins stores files related to a specific job. Each job has its own workspace, and it's where the job performs its work.

10. **SCM (Source Code Management):**
    SCM plugins in Jenkins enable integration with version control systems like Git, SVN, and others. They allow Jenkins to check out source code from a repository for building and testing.

11. **Plugin:**
    Plugins are extensions that add functionality to Jenkins. Jenkins has a vast plugin ecosystem, allowing users to integrate with various tools, version control systems, and services.

12. **Trigger:**
    A trigger is an event or condition that initiates the execution of a Jenkins job. Common triggers include code commits, scheduled builds, and manual initiation.

13. **Artifact:**
    An artifact is a file or set of files produced by a Jenkins job during the build process. Artifacts are typically the output of a build job and can be used for deployment or distribution.

14. **SCM Polling:**
    SCM polling is the process of periodically checking the version control system for changes. When changes are detected, Jenkins can trigger a build.

15. **Upstream and Downstream Jobs:**
    Jenkins jobs can be interconnected. An upstream job triggers a downstream job when it completes. Downstream jobs often rely on the artifacts produced by upstream jobs.

16. **Jenkinsfile:**
    A Jenkinsfile is a text file written in Groovy that defines the pipeline stages and steps for a Jenkins Pipeline job. It allows you to specify the entire build, test, and deployment process as code.

17. **Executor:**
    An executor is a computational resource on a node that can run Jenkins jobs. A single node can have multiple executors, allowing for concurrent job execution.

18. **Workspace Cleanup:**
    Workspace cleanup refers to the process of cleaning up the workspace of a job after it has completed its execution, freeing up disk space.

19. **Parameter:**
    Parameters allow you to pass dynamic values to your jobs, making them more versatile. For example, you can use parameters to specify a branch to build or a version number for deployment.