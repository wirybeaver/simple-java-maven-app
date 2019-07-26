// pipeline {
//     agent {
//         docker {
//             image 'maven:3-alpine' 
//             args '-v $HOME/.m2:/root/.m2' 
//         }
//     }
//     stages {
//         stage('Build') { 
//             steps {
//                 sh 'mvn -B -DskipTests clean package' 
//             }
//         }
//         stage('Test') {
//             steps {
//                 sh 'mvn test'
//             }
//             post {
//                 always {
//                     junit 'target/surefire-reports/*.xml'
//                 }
//             }
//         }
//         stage('Deliver') {
//             steps {
//                 sh './jenkins/scripts/deliver.sh'
//             }
//         }
//     }
// }

pipeline {
    stages {
        stage('Deliver') {
            when {
                branch 'master'
            }
            steps {
                sh "curl -XPOST -H'Content-Type: application/json' -d @$HOME/gitcode/wirynote/DruidKafka/aar.json http://localhost:8081/druid/indexer/v1/supervisor"
            }
        }
    }
}