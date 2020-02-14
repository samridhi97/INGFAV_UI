pipeline {
   agent any
	stages {
      stage('SCM Checkout') {
         steps {
            git 'https://github.com/samridhi97/INGFAV_UI.git'
		}
	}
	stage('Build') {
		steps {
			sh '''
			npm install
			npm run build
			npm audit fix
			'''
		}
	}
	stage ('Deploy') {
		steps {
			sh '''
             cp -r $WORKSPACE/build /opt/apache-tomcat-9.0.31/webapps
             curl -u admin:admin http://3.12.154.38:8888/manager/reload?path=/build 
             '''
		}
	}
}
}
