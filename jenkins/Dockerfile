FROM jenkins/jenkins:lts-jdk17

# Change to root user
USER root
RUN apt-get update && apt-get upgrade -y && apt-get autoremove -y

ENV JENKINS_ADMIN_USERNAME="root"
ENV JENKINS_ADMIN_PASSWORD="root"

# Skip setup wizard
ENV JAVA_OPTS="-Djenkins.install.runSetupWizard=false"

# Get plugins
COPY --chown=jenkins:jenkins plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN jenkins-plugin-cli -f /usr/share/jenkins/ref/plugins.txt

# Add groovy scripts to Jenkins hook
COPY --chown=jenkins:jenkins init.groovy.d/ /var/jenkins_home/init.groovy.d/

# Change to jenkins user
USER jenkins
