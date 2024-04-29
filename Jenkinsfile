pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('pmd') { 
            steps {
                sh 'mvn pmd:pmd' 
            }
        }
        stage('Doc') {
            steps {
                sh 'mvn javadoc:javadoc --fail-never'
            }
        }
        
        stage('Test report') {
            steps {
                sh 'mvn test --fail-never'
                sh 'mvn surefire-report:report'
            }
        }
    }
}