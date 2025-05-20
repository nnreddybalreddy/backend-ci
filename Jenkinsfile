pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    stage('read the version'){
        steps{
            defpackageJson =readJSON file: 'package.json'
            defappVersion =packageJson.version
            echo "application version:  $appVersion"
        }
    }        
    stage('Install Dependencies') {
        steps {
            sh """
                npm install
                ls -ltr
                echo "application version:  $appVersion"
            """
        }
    }

    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
        success { 
            echo 'I will run when pipeline is success'
        }
        failure { 
            echo 'I will run when pipeline is failure'
        }
    }
}
