pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				sh 'mvn -B -DskipTests clean package'
			}
		}
		stage('Docs') {
			steps {
				sh 'mvn javadoc:javadoc'
			}
		}
		stage('pmd') {
			steps {
				sh 'mvn pmd:pmd'
			}
		}
		stage('Test report') {
			steps {
				junit 'target/surefire-reports/*.xml'
			}
		}
	}
	post {
		always {
			archiveArtifacts artifacts: '**/target/**/*docs*.jar', fingerprint: true
			archiveArtifacts artifacts: '**/target/**/*docs*.war', fingerprint: true
			archiveArtifacts artifacts: '**/target/**/pmd.html', fingerprint: true
		}
	}
}