pipeline{

    // triggers{
    //     pollSCM '* * * * *'
    // }

    options {
        timestamps()
        gitLabConnection('my-repo') 
      
    }
      tools {
        maven 'my-work-maven'
        jdk 'java-8-work'
    }
    agent any
    stages{
        stage("chekout"){
            steps{
                echo "========executing chekout========"
                deleteDir()
                checkout scm
            }
        }
        stage("bulid img"){
            steps{
                echo "========executing bulid img========"
                script{
                    sh "ls"
                    configFileProvider([configFile(fileId: 'my_settings.xml', variable: 'set')]) {
                    // sh "cd imageio-extensions && mvn -s ${set} deploy"
                    sh "cd imageio-extensions && mvn -s ${set} deploy versions:set -DnewVersion=[3.7]"
                    }
                    
                    // sh "ls"
                    // sh "mvn clean install"
                    echo sh(script: 'env|sort', returnStdout: true)
                    sh 'printenv' 
                }
            }
        }
    }
    
    
    post{
        success{
            script{
                echo "yes"
                // script{
                //     emailext    recipientProviders: [culprits()],
                //     subject: 'yes', body: 'ooooononononn',  
                //     attachLog: true
                // }     
            
            
                // gitlabCommitStatus(connection: gitLabConnection(gitLabConnection: 'my-repo' , jobCredentialId: ''),name: 'report'){
                //     echo "hi you"
                // }
            }
        }
        failure {
            
            script{
                echo "no"
            //     emailext   recipientProviders: [culprits()],
            //     subject: 'YOU ARE BETTER THEN THAT !!! ', body: 'Dear programmer, you have broken the code, you are asked to immediately sit on the chair and leave the coffee corner.',  
            //     attachLog: true
            // }      

            // gitlabCommitStatus(connection: gitLabConnection(gitLabConnection: 'my-repo' , jobCredentialId: ''),name: 'report'){
            //     echo "hi you"
             }

            
        }
    }
}