pipeline {
   agent any
	stages {
      stage('SCM Checkout') {
         steps {
            git 'https://github.com/AnanyaAnshudhar/Kalyanam-UI.git'
		}
	}
	stage('Build') {
		steps {
			sh '''
			npm install
			ng build --base-href=/matrimony/                      
			'''
		}
	}
	stage ('Deploy') {
		steps {
			sh '''
             cp -r $WORKSPACE/dist/matrimony /opt/apache-tomcat-9.0.31/webapps
             curl -u admin:admin http://3.133.131.141:8888/manager/reload?path=/build 
             '''
		}
	}
}
}
