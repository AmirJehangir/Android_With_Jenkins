pipeline {
    agent any
    
    stages {
        
   

        stage('Preparation') { 
            
             steps {
        // Compile the app and its dependencies
        git branch: 'JenkinsTest/TestBranch', credentialsId: 'amir', url: 'https://amirjehangir@bitbucket.org/systems_dev/merchantapp_android.git'
      }
         
        }
        
        stage('Clean Build') {
            
            steps {
                
                sh 'chmod +x gradlew'  
             sh './gradlew clean'  
            }
            
                   
        }
        
        
        
        
        stage('Build release ') {
            // parameters {
            //     credentials credentialType: 'org.jenkinsci.plugins.plaincredentials.impl.FileCredentialsImpl', defaultValue: '5d34f6f7-b641-4785-frd5-c93b67e71b6b', description: '', name: 'keystore', required: true
            // }
             steps {
                 
               sh './gradlew assembleRelease' 
             }
            
           
        }
      
        stage('Compile') {
             steps {
                archiveArtifacts artifacts: '**/*.apk', fingerprint: true, onlyIfSuccessful: true   
                 
             }
                      
        }
        
    }
}
