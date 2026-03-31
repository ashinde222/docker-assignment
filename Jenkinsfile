pipeline {
		 agent{
                 	label{
                    		label "buildt-in"                	     }
        		}
    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/ashinde222/docker-assignment.git'
            }
        }

        stage('Cleanup Old Containers') {
            steps {
                sh 'docker rm -f c1 c2 c3 || true'
            }
        }

        stage('Deploy Q1') {
            steps {
                sh '''
                git checkout 2026-Q1
                docker run -d -p 80:80 --name c1 httpd
                docker cp index.html c1:/usr/local/apache2/htdocs/index.html
                docker exec c1 chmod -R 777 /usr/local/apache2/htdocs/index.html
                '''
            }
        }

        stage('Deploy Q2') {
            steps {
                sh '''
                git checkout 2026-Q2
                docker run -d -p 90:80 --name c2 httpd
                docker cp index.html c2:/usr/local/apache2/htdocs/index.html
                docker exec c2 chmod -R 777 /usr/local/apache2/htdocs/index.html
                '''
            }
        }

        stage('Deploy Q3') {
            steps {
                sh '''
                git checkout 2026-Q3
                docker run -d -p 9080:80 --name c3 httpd
                docker cp index.html c3:/usr/local/apache2/htdocs/index.html
                docker exec c3 chmod -R 777 /usr/local/apache2/htdocs/index.html
                '''
            }
        }
    }
}

