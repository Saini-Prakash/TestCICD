pipeline{
            agent any
            stages {
                    stage('feature') {
                            when {
                                allOf{
                                branch 'feature/*'
                                // changeset "force-app/**"
                                stage('Checkout'){
                                checkout scm
                                }
                                }
                            }
                
                    }
                }
}