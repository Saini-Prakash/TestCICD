pipeline{
            agent any
            stages {
                    stage('feature') {
                            when {
                                allOf{
                                branch 'qa'
                                // changeset "force-app/**"
                                stage('Checkout'){
                                checkout scm
                                }
                                }
                            }
                
                    }
                }
}