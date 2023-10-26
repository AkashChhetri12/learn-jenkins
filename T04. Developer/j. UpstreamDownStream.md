#  Upstream and Downstream jobs

In Jenkins, upstream and downstream jobs are used to create relationships between different jobs or pipelines. These relationships determine the order in which jobs are executed and enable passing artifacts, triggering subsequent jobs, and ensuring a coordinated build and deployment process.

Here are the concepts of upstream and downstream jobs, along with steps and an example:

1. **Upstream Job:**
   - An upstream job is a Jenkins job that triggers one or more downstream jobs. It is typically the initiating job in a build or deployment process.
   - Upstream jobs can pass build artifacts or other information to downstream jobs.
   - Upstream jobs can trigger downstream jobs upon successful completion, failure, or other conditions.

2. **Downstream Job:**
   - A downstream job is a Jenkins job that is triggered by one or more upstream jobs.
   - Downstream jobs often rely on the output (e.g., compiled binaries, test results) of their upstream jobs.
   - They can be configured to run after the completion of specific upstream jobs.

**Steps to Create Upstream and Downstream Jobs:**

1. **Create Upstream Job:**
   - Create a Jenkins job that serves as the upstream job. This job can be a Freestyle project, a Pipeline job, or any other Jenkins job type.

2. **Configure Upstream Job:**
   - In the configuration of the upstream job, specify the conditions under which downstream jobs should be triggered. You can configure this in the "Post-build Actions" section.

   - For example, you can use the "Build other projects" post-build action and specify the downstream jobs you want to trigger. You can define conditions, such as triggering the downstream job only when the upstream job succeeds.

3. **Create Downstream Jobs:**
   - Create one or more Jenkins jobs that will serve as downstream jobs. These jobs typically depend on the output or artifacts produced by the upstream job.

4. **Configure Downstream Jobs:**
   - In the configuration of each downstream job, you can specify the upstream job that should trigger it. This is done in the "Build Triggers" or "Build after other projects are built" section.

   - You can select the "Build when an upstream project is built" option and specify the upstream job(s) that should trigger the downstream job.

**Example:**

Let's consider an example in which you have a Java application, and you want to create a Jenkins pipeline with upstream and downstream jobs for building and deploying the application.

1. **Upstream Job (Build Job):**
   - Create an upstream job named "Build Job" that compiles and packages the Java application.

   - In the job configuration, specify that it should trigger downstream jobs upon a successful build.

2. **Downstream Job 1 (Unit Test):**
   - Create a downstream job named "Unit Test Job" that is triggered by the "Build Job."

   - In the job configuration, specify that it should only run if the "Build Job" succeeds.

   - Configure the "Unit Test Job" to execute unit tests on the compiled application.

3. **Downstream Job 2 (Deploy to Dev):**
   - Create another downstream job named "Deploy to Dev Job" that is triggered by the "Build Job."

   - In the job configuration, specify that it should only run if the "Build Job" succeeds.

   - Configure the "Deploy to Dev Job" to deploy the built application to a development environment.

This creates a pipeline where the "Build Job" is the upstream job, and "Unit Test Job" and "Deploy to Dev Job" are downstream jobs. The downstream jobs will only be executed if the "Build Job" succeeds. This ensures a coordinated and automated build, test, and deployment process.

By setting up upstream and downstream relationships, you can create complex and efficient build and deployment pipelines that handle dependencies and ensure proper execution order.



### Implementation of Upstream Downstream Job

To create a DSL pipeline that visualizes the example with upstream and downstream jobs, we'll need to create three separate Jenkinsfiles for the three different jobs: Build Job, Unit Test Job, and Deploy to Dev Job. Below are the Jenkinsfile configurations for each job.

### Build Job (Upstream Job) Jenkinsfile:
```groovy
// Build Job (Upstream Job)
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Compiling and packaging the Java application'
                // Add build steps here
            }
        }
    }
    post {
        success {
            build 'Unit Test Job'
            build 'Deploy to Dev Job'
        }
    }
}
```

The `post` block in the Build Job Jenkinsfile specifies that both the Unit Test Job and Deploy to Dev Job should be triggered upon successful completion of the Build Job.

### Unit Test Job Jenkinsfile:
```groovy
// Unit Test Job (Downstream Job 1)
pipeline {
    agent any
    stages {
        stage('Unit Test') {
            steps {
                echo 'Running unit tests on the Java application'
                // Add unit testing steps here
            }
        }
    }
}
```

The Unit Test Job Jenkinsfile only contains the configuration for running unit tests.

### Deploy to Dev Job Jenkinsfile:
```groovy
// Deploy to Dev Job (Downstream Job 2)
pipeline {
    agent any
    stages {
        stage('Deploy to Dev') {
            steps {
                echo 'Deploying the Java application to the development environment'
                // Add deployment steps here
            }
        }
    }
}
```

The Deploy to Dev Job Jenkinsfile only contains the configuration for deploying the application to the development environment.
