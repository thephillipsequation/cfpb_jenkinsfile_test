pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                withEnv(["GRADLE_HOME=${tool name: 'gradle4', type: 'hudson.plugins.gradle.GradleInstallation'}"]) {
                    withEnv(["PATH=${env.PATH}:${env.GRADLE_HOME}/bin"]) {
                        // Checking the env
                        echo "GRADLE_HOME=${env.GRADLE_HOME}"
                        echo "PATH=${env.PATH}"
                        sh "gradle ${params.GRADLE_TASKS_OPTIONS}"
                        sh "env|sort"
                    }
                }
            }
        }
    }
}
