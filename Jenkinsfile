pipeline {
    agent { node (label: 'agent-01' )}
        
        stages {
            stage('Build') {
                steps {
                    echo 'Building..'
                }
            }
            stage('Test'){
                steps {
                    echo 'Testing..'
                }
            }
        }    
}

**************
    pipeline { 
    agent any 
   
    stages {
        
        stage('Build') { 
            input{
                message "Should we proceed"
                submitter "user001"
                submitterParameter "approver" 
            }
            steps { 
                
                echo 'Building' 
            }
        }
        stage('Test'){
            input{
                message "Should we proceed"
                submitter "user001"
                submitterParameter "approver" 
            }
            steps {
                echo 'Testing'
            }
        }
        stage('Deploy') {
            input{
                message "Should we proceed"
                submitter "user001"
                submitterParameter "approver" 
            }
            steps {
                echo 'Deploying'
            }
        }
    }
}

************
    node{
    stage('Build'){
         properties([
        parameters([
            password(name: 'AccountMaster', description: 'To continue the process, sign in with an Master Password')
        ])
    ])
    def usernameLocal, passwordLocal
    withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: "A16R12P93", 
    passwordVariable: 'PASSWORD', usernameVariable: 'USERNAME']]){
        //usernameLocal = env.USERNAME
        passwordLocal = env.PASSWORD
    }
        if("$passwordLocal" == "$AccountMaster"){
            echo "Your process is running"
        }else{
           echo "Your process is not running. Contact your System Manager to provide permission." 
        }
    }
}


echo "$usernameLocal2"
    if("$usernameLocal2" == "$usernameLocal"){
        echo "The job was approved by a Master User and is running."
    }else{
        echo "The job was not approved by a Master User and was aborted."
    }

**********************
    pipeline {
    agent any
    stages{
        stage('Build Approval') {
            steps{
                script{
                    if("$ProcessControl" == "No"){
                        echo "The building process was aborted."
                        currentBuild.result = 'SUCCESS'
                    }else{
                        def usernameLocal, passwordLocal, usernameLocal2
                        withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: "A16R12P93", 
                        passwordVariable: 'PASSWORD', usernameVariable: 'USERNAME']]){
                            usernameLocal = env.USERNAME
                            //passwordLocal = env.PASSWORD
                        }
                        wrap([$class: 'BuildUser']) {
                            usernameLocal2 = "$BUILD_USER_ID"
                        }
                        echo "$usernameLocal"
                        echo "$usernameLocal2"
                        
                        if("$usernameLocal2" == "$usernameLocal"){
                            echo "The job was approved by a Master User and is running."
                        }else{
                            echo "The job was not approved by a Master User and was aborted."
                        }
                    }
                }
            }
        }
        stage('Test'){
            steps{
                echo "Testing."
            }
        }
        stage('Deploy'){
            steps{
                echo "Deploying."
            }
        }
    }
}


 


