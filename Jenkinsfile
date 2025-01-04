@Library('my-shared-library@main') _

pipeline {
    agent { label 'slave-1' }

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64'
        MAVEN_HOME = '/usr/share/maven'
        PATH = "${JAVA_HOME}/bin:${MAVEN_HOME}/bin:${env.PATH}"
    }

   stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Set up Java 17') {
            steps {
                script {
                pipeline.setupjava()
                }
            }
        }

        stage('Set up Maven') {
            steps {
                script {
                pipeline.mavensetup()
				}
            }
        }

        stage('Build with Maven') {
            steps {
                script {
                pipeline.build()
				}
            }
        }

        stage('Upload Artifact') {
            steps {
                uploadArtifact('target/bus-booking-app-1.0-SNAPSHOT.jar')
            }
        }

        stage('Run Application') {
            steps {
                script {
                pipeline.runApp()
				}
            }
        }

        stage('Validate App is Running') {
            steps {
                script {
                pipeline.validateApp()
				}
            }
        }
        stage('wait') {
			steps {
				script {
					pipeline.wait()
				}
			}
        }
        stage('stoping') {
			steps {
				script {
					pipeline.stop()
				}
			}
        }
         stage('cleaning') {
			steps {
				script {
					pipeline.clean()
				}
			}
        }        
		stage('sending a mail') {
			steps {
				script {
				pipeline.mail()
			}
			}
        }
    }
}
