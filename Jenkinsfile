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
                script {
                checkoutscm()
                }
            }
        }

        stage('Set up Java 17') {
            steps {
                script {
                setupjava()
                }
            }
        }

        stage('Set up Maven') {
            steps {
                script {
                mavensetup()
				}
            }
        }

        stage('Build with Maven') {
            steps {
                script {
                build()
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
                runApp()
				}
            }
        }

        stage('Validate App is Running') {
            steps {
                script {
                validateApp()
				}
            }
        }
        stage('wait') {
			steps {
				script {
					wait()
				}
			}
        }
        stage('stoping') {
			steps {
				script {
					stop()
				}
			}
        }
         stage('cleaning') {
			steps {
				script {
					clean()
				}
			}
        }        
		stage('sending a mail') {
			steps {
				script {
				mail()
			}
			}
    }
  }
}
