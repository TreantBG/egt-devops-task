pipeline {
    agent {
        docker {
            image 'maven:3.6-openjdk-8' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Test') { 
            steps {
                sh 'mvn test' 
            }
        }

        stage('Build') { 
            steps {
                sh 'mvn clean install -Dmaven.test.skip=true' 
            }
        }

        stage('Publish') { 
            steps {
                nexusPublisher nexusInstanceId: 'nx3', nexusRepositoryId: 'maven-releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: './target/spring-boot-mysql-*.jar']], mavenCoordinate: [artifactId: 'fancyWidget', groupId: 'com.mycompany', packaging: 'jar', version: '1.1']]], tagName: '${env.BUILD_NUMBER}'
            }
        }
    }
}