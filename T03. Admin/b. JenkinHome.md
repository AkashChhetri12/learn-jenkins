# Jenkins Home - Files and Folder Structure

The Jenkins home directory is the central location where Jenkins stores all of its configuration, job definitions, build histories, and other important data. The exact location of the Jenkins home directory may vary depending on your installation method and operating system, but it's commonly found at `/var/lib/jenkins` on Linux systems. Below is the typical structure of Jenkins files and folders within the Jenkins home directory:

1. **config.xml:**
   - This XML file contains the overall configuration of the Jenkins server, including system settings and security configurations.

2. **jobs/:**
   - The "jobs" directory contains subdirectories, each representing a Jenkins job (also called projects or builds). Each job folder contains configuration files and build data.

3. **nodes/:**
   - In the "nodes" directory, Jenkins stores configuration and runtime data for build nodes (agents). Each node has its subdirectory for workspace and metadata.

4. **secrets/:**
   - This directory stores sensitive information and secrets, such as encryption keys and credentials, securely. This data should be treated with care.

5. **workspace/:**
   - For each job, Jenkins creates a subdirectory within the "workspace" directory where the job-specific files are stored during the build process. These files are used for the build and may include source code, build artifacts, and logs.

6. **userContent/:**
   - Jenkins allows users to add static files (e.g., CSS, JavaScript, images) for customizing the Jenkins UI and job pages. These files are placed in the "userContent" directory.

7. **plugins/:**
   - The "plugins" directory stores Jenkins plugins. Each plugin is typically stored in its own subdirectory, which contains the plugin's .jpi and .hpi files, among other artifacts.

8. **updates/:**
   - This directory contains Jenkins update files, including metadata about available updates and downloaded plugin data.

9. **workspace-cleanup.log:**
   - A log file that records workspace cleanup activities. Jenkins can be configured to clean up workspace directories after a job finishes.

10. **config-history/:**
    - If the Configuration History plugin is installed, it keeps track of configuration changes and saves historical versions of the Jenkins configuration.

11. **fingerprints/:**
    - Jenkins maintains fingerprints of build artifacts to track their usage across different jobs.

12. **logs/:**
    - Jenkins log files, including logs for the Jenkins server and individual job logs, are stored in the "logs" directory.

13. **userContent/:**
    - Users can upload custom files and resources for display within Jenkins job pages and the Jenkins user interface.

14. **users/:**
    - User information is stored in individual subdirectories within the "users" directory.

15. **secrets/:**
    - Secure information and credentials, such as API tokens, are stored in this directory.

16. **jobs/{job_name}/:**
    - Each job's subdirectory contains job-specific configuration files, build artifacts, and logs.

The structure of the Jenkins home directory ensures that all configuration and data are organized in a way that makes it easy to manage and maintain Jenkins. 