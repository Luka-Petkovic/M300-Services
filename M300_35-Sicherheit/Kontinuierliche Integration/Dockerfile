# Verwenden Sie das offizielle Jenkins Blue Ocean Image als Basis
FROM jenkinsci/blueocean

# Setzen Sie den Benutzer auf root, um zusätzliche Pakete zu installieren
USER root

# Installieren Sie Maven
RUN apk add --no-cache maven

# Setzen Sie den Benutzer zurück auf jenkins
USER jenkins

# Kopieren Sie die Jenkins-Pipeline-Datei (Jenkinsfile) in das Arbeitsverzeichnis
COPY Jenkinsfile /var/jenkins_home/workspace/Jenkinsfile

# Setzen Sie das Arbeitsverzeichnis auf den Jenkins-Workspace
WORKDIR /var/jenkins_home/workspace

# Führen Sie die Jenkins-Pipeline aus
RUN /usr/local/bin/jenkins.sh
