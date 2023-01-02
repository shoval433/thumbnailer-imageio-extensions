pipeline{

    // triggers{
    //     pollSCM '* * * * *'
    // }

    options {
        timestamps()
        gitLabConnection('my-repo') 
      
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
                    sh "cd imageio-extensions"
                    sh "ls"
                    sh "mvn clean install"
                    
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