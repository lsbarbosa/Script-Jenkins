pipeline{
agent any

stages{

    stage('checkout scm') {
        steps {
            script{
                git credentialsId: '8bd8-419d-8af0-30960441fcd7', url: 'ssh://jenkins@git.company.com:/usr/company/repositories/repo.git'
                sh 'git branch -r | awk \'{print $1}\' ORS=\'\\n\' >>branch.txt'
            }

        }
    }
     stage('get build Params User Input') {
        steps{
            script{

                liste = readFile 'branch.txt'
                echo "please click on the link here to chose the branch to build"
                env.BRANCH_SCOPE = input message: 'Please choose the branch to build ', ok: 'Validate!',
                        parameters: [choice(name: 'BRANCH_NAME', choices: "${liste}", description: 'Branch to build?')]


            }
        }
    } 
    stage("checkout the branch"){
        steps{
            echo "${env.BRANCH_SCOPE}"
            git  credentialsId: 'ea346a50-8bd8-419d-8af0-30960441fcd7', url: 'ssh://jenkins@git.company.com/usr/company/repositories/repo.git'
            sh "git checkout -b build ${env.BRANCH_NAME}"
        }
    }
    stage(" exec maven build"){
        steps{
            withMaven(maven: 'M3', mavenSettingsConfig: 'mvn-setting-xml') {
               sh "mvn clean install "
            }
        }
    }
    stage("clean workwpace"){
        steps{
            cleanWs()
        }
    }
}
}
