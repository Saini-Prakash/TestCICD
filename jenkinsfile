pipeline{
            agent any
            environment{
                SF_ORG_AUTH_URL = credentials('SF_ORG_AUTH_URL')
                GIT_USERNAME = credentials('GIT_USERNAME')
            }
            stages {
                    stage('feature') {
                            when {
                                allOf{
                                branch 'feature/*'
                                // changeset "force-app/**"
                                }
                            }
                        stages{
                                stage('validate_against_QA'){
                                    agent any
                                    steps {
                                         withCredentials([usernamePassword(credentialsId: 'a1be5577-684d-4e8c-b9db-0afe99a36c37', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USER')]) {
                                            sh 'git config http.sslVerify "false"'
                                            sh 'git config credential.username "${GIT_USER}"'
                                            sh(returnStdout: true, script: 'git config credential.helper "!echo password=${GIT_PASSWORD}; echo"')
                                            script{
                                                fetch_all_tags = sh(script: 'git fetch --tags', , returnStdout: true).trim()
                                                qa_tag = sh(script: 'git describe --match "qa-*" --abbrev=0 --tags HEAD', , returnStdout: true).trim()
    
                                            }
                                            sh "echo $SF_ORG_AUTH_URL > authURLFile"
                                            sh "sfdx force:auth:sfdxurl:store -f authURLFile -s -a QA"
                                            }
                                            
                                        }
                                }
                        }
                    }
                }
}
