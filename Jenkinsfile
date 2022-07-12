pipeline{
            agent any
            environment{
                SF_ORG_AUTH_URL = credentials('SF_ORG_AUTH_URL')
                GIT_USERNAME = credentials('GIT_USERNAME')
            }
            stage('Checkout'){
                Checkout scm
            }
}