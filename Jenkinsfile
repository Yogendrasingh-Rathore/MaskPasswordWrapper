pipeline
{
    agent any
               
        stages{
            stage('build'){
                steps{
                                         
                        wrap([$class: 'MaskPasswordsBuildWrapper', varPasswordPairs: [[password: '123ADS', var: 'SECRET']]]) 
                        {
                            echo env['SECRET'];
                        }
                     }
            }        
        }

        post{

            success{
                       emailext (
                                    subject: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                                    body: """
                                    STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':
                                    Check console output at "${env.JOB_NAME} [${env.BUILD_NUMBER}]"
                                    """,
                                    recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                                )
                    }
                
            

            failure{
                
                  emailext (
                                    subject: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                                    body: """
                                    STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':
                                    Check console output at "${env.JOB_NAME} [${env.BUILD_NUMBER}]"
                                    """,
                                    recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                            )
                  }
        }
}