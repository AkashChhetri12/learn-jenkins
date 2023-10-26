# Parameterized pipelines in Jenkins
Creating parameterized pipelines in Jenkins allows you to customize job runs with user-defined values or options. Here's how to create parameterized Freestyle, DSL, and Scripted pipelines:

### Parameterized Freestyle Pipeline:

1. **Access Jenkins Dashboard:**
   - Log in to your Jenkins server and access the dashboard.

2. **Create a New Freestyle Project:**
   - Click on "New Item" to create a new project.
   - Enter a name for your project and select "Freestyle project."
   - Click "OK."

3. **Configure the Project:**
   - In your project's configuration page, scroll down to the "Build" section.

4. **Add Parameters:**
   - Click on the "This project is parameterized" checkbox to enable parameters.
   - Click the "Add Parameter" dropdown to select the type of parameter you want (e.g., String, Choice, Boolean, etc.).
   - Configure the parameter with a name and options.

5. **Use Parameters in Build Steps:**
   - In your build steps or scripts, you can use the defined parameters using the format `$PARAMETER_NAME` (e.g., `$MY_PARAMETER`).

6. **Save the Configuration:**
   - Save your project configuration.

### Parameterized DSL Pipeline:

For a parameterized DSL pipeline, you'll need to define parameters in your pipeline script. Here's an example of a parameterized DSL pipeline:

```groovy
pipeline {
    agent any
    parameters {
        string(name: 'TARGET_ENV', defaultValue: 'dev', description: 'Target environment: dev, qa, prod')
        booleanParam(name: 'DEBUG', defaultValue: false, description: 'Enable debug mode')
    }
    stages {
        stage('Build') {
            steps {
                echo "Building for ${params.TARGET_ENV} environment."
            }
        }
        stage('Deploy') {
            steps {
                sh "deploy_script.sh --env ${params.TARGET_ENV} --debug ${params.DEBUG}"
            }
        }
    }
}
```

In this example, the pipeline defines two parameters: `TARGET_ENV` and `DEBUG`. You can customize the pipeline run by providing values for these parameters.

### Parameterized Scripted Pipeline:

For a parameterized Scripted pipeline, you can also define parameters in the script. Here's an example:

```groovy
node {
    properties([
        parameters([
            string(name: 'TARGET_ENV', defaultValue: 'dev', description: 'Target environment: dev, qa, prod'),
            booleanParam(name: 'DEBUG', defaultValue: false, description: 'Enable debug mode')
        ])
    ])
    
    stage('Build') {
        echo "Building for ${TARGET_ENV} environment."
    }
    
    stage('Deploy') {
        sh "deploy_script.sh --env ${TARGET_ENV} --debug ${DEBUG}"
    }
}
```

This example defines the same parameters, `TARGET_ENV` and `DEBUG`, and uses them in the pipeline.

When you trigger a parameterized DSL or Scripted pipeline, Jenkins will prompt you to provide values for the defined parameters before the job starts. This allows for flexibility and customization of each pipeline run.