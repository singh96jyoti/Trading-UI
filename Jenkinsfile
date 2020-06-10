pipeline {
   agent any
	stages {
      stage('SCM Checkout') {
         steps {
            git 'https://github.com/singh96jyoti/TRADING-UI.git'
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
             cp -r $WORKSPACE/build /opt/apache-tomcat-9.0.36/webapps
             curl -u admin:admin http://18.221.162.82:8888/manager/reload?path=/build 
             '''
		}
	}
}
}
