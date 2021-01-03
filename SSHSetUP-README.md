# tomcat-deployment-withJenkinsCICD

# Pre-Requisites:
    Jenkins Server
    Tomcat Server
    Install GIT and Maven in Jenkins Server
# Tomcat Server
  ![image](https://user-images.githubusercontent.com/58024415/103478357-1e3f0800-4dec-11eb-8fd0-f4ad9cf58cfb.png)
# Jenkins Server
  ![image](https://user-images.githubusercontent.com/58024415/103478368-34e55f00-4dec-11eb-8a88-e846572acef0.png)
# Login to Jenkins user and Generate SSH key in Jenkins server
    su -s /bin/bash jenkins
    ssh-keygen
  ![image](https://user-images.githubusercontent.com/58024415/103479146-b4296180-4df1-11eb-8b26-8993f69b93e1.png)
# Copy public key to tomcat server at "/root/.ssh/authorized_keys"
    vi /root/.ssh/authorized_keys
# Enable sudo permission for jenkins user in jenkins server
    visudo
    ----------------------------------------------------------
    jenkins ALL=(ALL)       NOPASSWD: ALL
    ----------------------------------------------------------
  ![image](https://user-images.githubusercontent.com/58024415/103479253-6f51fa80-4df2-11eb-9e35-a0bb65839e5a.png)
# Enable passAuthentication at "/etc/ssh/sshd_config" in both the servers
    vi /etc/ssh/sshd_config
    ----------------------------------------------------------
    PasswordAuthentication yes
    ----------------------------------------------------------
# Connection need to be done from jenkins server to tomcat server
  ssh root@<IP of tomcat-server>
    
    ssh root@3.236.240.247
# Send file from jenkins server to tomcat server
    touch test.txt
    scp test.txt root@3.236.240.247:/opt
# Create jenkins job and copy jenkinsfile content in pipeline section
  ![image](https://user-images.githubusercontent.com/58024415/103479623-fc964e80-4df4-11eb-8d8d-7cb47b80d5bc.png)
  
  Click on build
# Check in UI for Output of applicaiton
  http://3.236.240.247:8080/mavewebappdemo-2.0.0-SNAPSHOT/
  
  ![image](https://user-images.githubusercontent.com/58024415/103479635-1c2d7700-4df5-11eb-9d53-7f02e245fd43.png)
