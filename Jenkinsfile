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
                      mail bcc: '', body: "SUCCESS : Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' Check console output at '${env.JOB_NAME} [${env.BUILD_NUMBER}]' ",
                      cc: '', from: 'yogendrasingh.rathore@cuelogic.com', replyTo: '', subject: "SUCCESS : Job \'${env.JOB_NAME} [${env.BUILD_NUMBER}]\'", to: 'yogendrasingh.rathore@cuelogic.com'
                                
                    }
                
            

            failure{
                
                      mail bcc: '', body: "FAILED : Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' Check console output at '${env.JOB_NAME} [${env.BUILD_NUMBER}]' ",
                      cc: '', from: 'yogendrasingh.rathore@cuelogic.com', replyTo: '', subject: "FAILED : Job \'${env.JOB_NAME} [${env.BUILD_NUMBER}]\'", to: 'yogendrasingh.rathore@cuelogic.com'
                            
                  }
        }
}
