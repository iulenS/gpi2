pipeline {
    stages {
        stage('git') {
	    steps { git url: 'https://github.com/iulenS/gpi2' }
        }
        stage('Build') {
	    steps {
	        sh 'mvn -B -DskipTests clean package'
	        echo 'Compilando Maven...'
		dir('proyecto_scca/plataforma_integracion_y_gestion/simple') {
		    sh 'mvn compile'
		    sh 'mvn test'
		    sh 'mvn site'
		    sh 'mvn verify'
		}
		echo 'Compilando Android...'
	        dir('app_android/ApplicationA115670'){
		    sh './gradlew tasks'
		    sh './gradlew check'
		}
	        echo 'Compilando Arduino...'
		dir('proyecto_scca/sensores/FooProject'){
		    sh 'make'
		}
	    }
	}
    }
}
