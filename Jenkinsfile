pipeline{

    agent any

    stages {

        stage ('Compile Stage') {

            steps {

                withMaven(maven: 'maven_3_5_0') {
					where java
					where javac
					java -version
					javac -version
					mvn --version
					echo $JAVA_HOME
                    bat 'mvn clean install'
					
                }

            }
        }
    stage ('Test Stage') {

            steps {

                withMaven(maven: 'maven_3_5_0') {
                    bat 'mvn test'

                }

            }
        }


        stage ('Cucumber Reports') {

            steps {
                cucumber buildStatus: "UNSTABLE",
                    fileIncludePattern: "**/cucumber.json",
                    jsonReportDirectory: 'target'

            }

        }

    }

}