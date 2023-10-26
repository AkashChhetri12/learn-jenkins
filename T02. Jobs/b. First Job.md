# First Job [Freestyle]

First Freestyle Project job in Jenkins:

1. **Access the Jenkins Dashboard:**
   - Open your web browser and go to the Jenkins web interface. Typically, it's available at `http://localhost:8080` if Jenkins is installed on your local machine. Replace `localhost` with your Jenkins server's address if needed.

2. **Create a New Job:**
   - Click on "New Item" on the left-hand side of the Jenkins dashboard.

3. **Enter Job Details:**
   - Enter a name for your job in the "Item name" field. This name should be descriptive and help you identify the purpose of the job.
   - Select "Freestyle project" as the project type.
   - Click "OK" to create the job.

4. **Configure Your Freestyle Project:**
   - You will be taken to the configuration page for your new Freestyle Project.

5. **General Configuration:**
   - In the "General" section, you can provide a brief description of your job if needed.

6. **Build Configuration:**
   - In the "Build" section, click on the "Add build step" dropdown and select "Execute shell" (if you're on a Unix-like system) or "Execute Windows batch command" (if you're on Windows).
   - In the command box that appears, enter a simple shell or batch command. For example, you can use the "echo" command to print a message:

   For Unix/Linux:
   ```bash
   echo "Hello, Jenkins! This is your first job."
   ```

   For Windows:
   ```batch
   echo Hello, Jenkins! This is your first job.
   ```

7. **Save Your Configuration:**
   - Scroll down to the bottom of the configuration page and click "Save" to save your job configuration.

8. **Build Your Job:**
   - After saving your job, you can manually build it by clicking "Build Now" on the job's page. You can also configure triggers to automate builds based on events like code commits.

9. **View the Console Output:**
   - You can see the progress and output of your job by clicking on the build number under the "Build History" section on the job's page. This will take you to the console output, where you can view the result of your shell or batch command.
