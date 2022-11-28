pipeline {
    agent any
    stages {
        stage("Prepare") {
            steps {
                echo("Start Job : ${env.JOB_NAME}")
                echo("Start Build : ${env.BUILD_NUMBER}")
                echo("Branch NAme : ${env.BRANCH_NAME}")
            }
        }
        stage("Build") {
            steps {
                script {
                    for(int i = 0; i < 10; i++){
                        echo("Script ${i}")
                    }
                }

                echo("Start Build")
                sh("./mvnw clean compile test-compile")
                echo("Finish Build")
            }
        }
        stage("Test"){
            steps {
                script {
                    def data = [
                        "firstName" : "Abdul",
                        "lastName" : "Aziz"
                    ]
                    writeJSON(file: "data.json", json: data)
                }
                echo("Start Test")
                sh("./mvnw test")
                echo("Finish Test")
            }
        }
        stage("Deploy"){
            steps {
                echo "Hello Deploy 1"
                sleep(5)
                echo "Hello Deploy 2"
                echo "Hello Deploy 3"
            }
        }
    }
    post {
        always {
            echo "I will always Hello again!"
        }
        success {
            echo "Yay, success!"
        }
        failure {
            echo "Oh no, failure"
        }
        cleanup {
            echo "Don't care success or error"
        }
    }
}