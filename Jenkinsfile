pipeline { 
    agent any

    stages {
        stage('Echo') {
            steps {
                echo 'Testing...'
            }
        stage('Scripted Signature test') {
            steps {
                script {
                    def foo = Result.fromString('FAILURE')
                }
            }
        }
    }
}
