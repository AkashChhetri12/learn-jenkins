# Install and Configure Jenkins

Jenkins can be installed and configured on various platforms, including Linux, Windows, using a standalone WAR file, or within a Docker container. Below, I'll provide step-by-step instructions for installing and configuring Jenkins in each of these scenarios.

### Installation and Configuration on Linux:

1. **Prerequisites:**
   - A Linux server or VM.
   - Java Runtime Environment (JRE) installed (Jenkins requires Java 8 or later).

2. **Install Jenkins:**
   - Open a terminal on your Linux machine.
   - Run the following commands to add the Jenkins repository and install Jenkins:

   ```bash
   sudo apt update
   sudo apt install -y openjdk-11-jre     # Install Java (adjust for your version)
   wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
   sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
   sudo apt update
   sudo apt install -y jenkins
   ```

3. **Start Jenkins:**
   - Start the Jenkins service and enable it to start on boot with the following commands:

   ```bash
   sudo systemctl start jenkins
   sudo systemctl enable jenkins
   ```

4. **Access Jenkins:**
   - Open a web browser and go to `http://<your-server-IP>:8080` to access the Jenkins setup wizard. You'll find the initial admin password in the `/var/lib/jenkins/secrets/initialAdminPassword` file.

5. **Complete the Setup:**
   - Follow the setup wizard, providing the admin password, installing recommended plugins, and creating an admin user.

### Installation and Configuration on Windows:

1. **Prerequisites:**
   - A Windows machine or server.
   - Java Runtime Environment (JRE) installed (Jenkins requires Java 8 or later).

2. **Install Jenkins:**
   - Download the Windows installer from the Jenkins website (https://www.jenkins.io/download/).
   - Run the installer and follow the installation prompts.

3. **Start Jenkins:**
   - Jenkins will be automatically started as a Windows service during installation.

4. **Access Jenkins:**
   - Open a web browser and go to `http://localhost:8080` to access the Jenkins setup wizard.

5. **Complete the Setup:**
   - Follow the setup wizard, providing the admin password, installing recommended plugins, and creating an admin user.

### Installation and Configuration Using the WAR File:

1. **Prerequisites:**
   - Java Runtime Environment (JRE) installed (Jenkins requires Java 8 or later).

2. **Download Jenkins WAR File:**
   - Download the Jenkins WAR file from the Jenkins website (https://www.jenkins.io/download/).

3. **Run Jenkins:**
   - Open a terminal or command prompt.
   - Navigate to the directory where you downloaded the Jenkins WAR file.
   - Run Jenkins with the following command:

   ```bash
   java -jar jenkins.war
   ```

4. **Access Jenkins:**
   - Open a web browser and go to `http://localhost:8080` to access the Jenkins setup wizard.

5. **Complete the Setup:**
   - Follow the setup wizard, providing the admin password, installing recommended plugins, and creating an admin user.

### Installation and Configuration Using Docker:

1. **Prerequisites:**
   - Docker installed on your machine.

2. **Pull and Run Jenkins in a Docker Container:**
   - Open a terminal or command prompt.
   - Run the following Docker command to pull and run the Jenkins container:

   ```bash
   docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts
   ```

3. **Access Jenkins:**
   - Open a web browser and go to `http://localhost:8080` to access the Jenkins setup wizard.

4. **Retrieve the Admin Password:**
   - To retrieve the admin password, run the following command to view the container logs:

   ```bash
   docker logs <container_id>
   ```

   Look for the line that starts with "Jenkins initial setup is required."

5. **Complete the Setup:**
   - Follow the setup wizard, providing the admin password, installing recommended plugins, and creating an admin user.


Resource: 

* Jenkins official page -> https://www.jenkins.io/

* Jenkins Installation -> https://www.jenkins.io/doc/book/installing/

* Jenkins Plugin -> https://plugins.jenkins.io/

* Jenkins LTS changelogs -> https://www.jenkins.io/changelog-stable/

* Jenkis LTS artifact -> https://get.jenkins.io/war-stable/latest/
