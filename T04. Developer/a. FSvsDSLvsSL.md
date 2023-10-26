# Freestyle vs DSL vs Scripted Pipeline

Jenkins provides several ways to define and configure build and deployment pipelines. The three common methods are Freestyle projects, Declarative Pipeline DSL, and Scripted Pipeline DSL. I'll explain each with a simple example and steps for setting up a basic pipeline in each approach.

### Freestyle Project:

**Description:**
- Freestyle projects are the simplest and most user-friendly way to create Jenkins jobs.
- They use a graphical user interface for configuring the build process.

**Example:**
Let's create a Freestyle project that builds a basic Java application.

**Steps:**
1. **Access Jenkins Dashboard:**
   - Log in to the Jenkins dashboard.

2. **Create a New Job:**
   - Click "New Item" and enter a name for your project.
   - Choose "Freestyle project" and click "OK."

3. **Configure the Build:**
   - In the project configuration page, under the "Build" section, click "Add build step" and choose "Execute shell" (for Unix-like systems) or "Execute Windows batch command" (for Windows).
   - In the command box, enter a simple build command, such as compiling a Java program.

4. **Save the Configuration:**
   - Click "Save" to save the project configuration.

5. **Build the Job:**
   - Click "Build Now" to execute the job.

### Declarative Pipeline DSL:

**Description:**
- Declarative Pipelines use a more structured and domain-specific language for defining build and deployment pipelines.
- They are concise and easy to read, making them ideal for many use cases.

**Example:**
Here's a simple Declarative Pipeline that builds and tests a Java application.

**Steps:**
1. **Access Jenkins Dashboard:**
   - Log in to the Jenkins dashboard.

2. **Create a New Item:**
   - Click "New Item" and enter a name for your pipeline.
   - Choose "Pipeline" and click "OK."

3. **Configure the Pipeline:**
   - In the pipeline configuration page, scroll down to the "Pipeline" section.
   - Enter the pipeline script:

   ```groovy
   pipeline {
       agent any
       stages {
           stage('Build') {
               steps {
                   sh 'javac HelloWorld.java'
               }
           }
           stage('Test') {
               steps {
                   sh 'java HelloWorld'
               }
           }
       }
   }
   ```

4. **Save the Configuration:**
   - Click "Save" to save the pipeline configuration.

5. **Build the Pipeline:**
   - Click "Build Now" to execute the pipeline.

### Scripted Pipeline DSL:

**Description:**
- Scripted Pipelines provide the highest level of flexibility by allowing you to write pipelines as Groovy scripts.
- They are suitable for complex or dynamic build and deployment processes.

**Example:**
Here's a simple Scripted Pipeline that does the same as the previous example.

**Steps:**
1. **Access Jenkins Dashboard:**
   - Log in to the Jenkins dashboard.

2. **Create a New Item:**
   - Click "New Item" and enter a name for your pipeline.
   - Choose "Pipeline" and click "OK."

3. **Configure the Pipeline:**
   - In the pipeline configuration page, scroll down to the "Pipeline" section.
   - Enter the pipeline script:

   ```groovy
   node {
       stage('Build') {
           sh 'javac HelloWorld.java'
       }
       stage('Test') {
           sh 'java HelloWorld'
       }
   }
   ```

4. **Save the Configuration:**
   - Click "Save" to save the pipeline configuration.

5. **Build the Pipeline:**
   - Click "Build Now" to execute the pipeline.

