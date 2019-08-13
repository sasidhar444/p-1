node {
   def mvnHome
   stage('Preparation') {
    
      git 'https://github.com/Nish1989/simple-maven-project-with-tests.git'          
      mvnHome = tool 'M3'
   }
   stage('Build') {
      // Run the maven build
      withEnv(["MVN_HOME=$mvnHome"]) {
         sh '"$MVN_HOME/bin/mvn" -Dmaven.test.failure.ignore clean package'
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.jar'
   }
    stage('Ansible Deploy') {  
          sh 'ls -lrt'
          sh 'ansible --version'
          sh 'ansible all -m ping -i hosts'
          //sh 'ansible-playbook playbook.yml -i inventory -e ”host=cart app=cart” '
        }
}
