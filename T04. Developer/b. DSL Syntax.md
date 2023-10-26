# DSL Syntax

The syntax for defining Jenkins pipelines using the Declarative Pipeline DSL is based on a structured and human-readable format. 

A Declarative Pipeline script starts with the `pipeline` block and defines stages, steps, and other directives within it.

```groovy
pipeline {
    agent { ... } // Specifies where the pipeline will run (e.g., any, label, docker)
    options { ... } // Defines pipeline options (e.g., timeout, retry)
    environment { ... } // Sets environment variables
    parameters { ... } // Specifies input parameters for the pipeline (optional)

    stages {
        stage('Build') {
            steps {
                // Build steps here
            }
        }
        stage('Test') {
            steps {
                // Test steps here
            }
        }
        // Add more stages as needed
    }

    post {
        always {
            // Steps to execute after all stages
        }
        success {
            // Steps to execute when the pipeline is successful
        }
        failure {
            // Steps to execute when the pipeline fails
        }
    }
}
```

Here are the main components and syntax elements:

1. `pipeline { ... }`: The top-level block that encapsulates the entire pipeline script.

2. `agent { ... }`: Specifies where the pipeline will run, such as on any available agent, on an agent with a specific label, or in a Docker container.

3. `options { ... }`: Defines pipeline options, including timeout, retry, and other configuration settings.

4. `environment { ... }`: Sets environment variables that will be available to all steps in the pipeline.

5. `parameters { ... }`: (Optional) Defines input parameters for the pipeline. These parameters can be used to customize the pipeline behavior, such as choosing an environment or specifying a target branch.

6. `stages { ... }`: Contains a list of stages that define the high-level steps in the pipeline. Each stage can have one or more build steps.

7. `stage('Name') { ... }`: Defines a stage with a given name, and inside it, you can define a list of build steps using the `steps` block.

8. `steps { ... }`: Inside a stage, you specify the individual build steps, which can include shell commands, script executions, or specific build tools like `mvn`, `npm`, or `docker`.

9. `post { ... }`: Contains post-build actions to execute, such as clean-up tasks or notifications. You can specify actions for different conditions like `always`, `success`, and `failure`.

Here's an example of a complete Declarative Pipeline script:

```groovy
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'make'
            }
        }
        stage('Test') {
            steps {
                sh 'make test'
            }
        }
    }
    post {
        always {
            junit '**/target/test-*.xml'
        }
        success {
            mail to: 'team@example.com', subject: 'Pipeline Successful', body: 'The pipeline has succeeded.'
        }
        failure {
            mail to: 'team@example.com', subject: 'Pipeline Failed', body: 'The pipeline has failed.'
        }
    }
}
```

This Declarative Pipeline script checks out code, builds it, runs tests, and sends email notifications based on the outcome. You can adapt this syntax to define pipelines for your specific project requirements.