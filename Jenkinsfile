pipeline {

	// Jenkins 실행 에이전트
	agent any

	stages {

		// React 의존성 설치
		stage('Install Dependencies') {
			steps {
				sh '''
                    cd frontend
                    npm ci
                '''
			}
		}

		// React 프로젝트 빌드
		stage('Build React') {
			steps {
				sh '''
                    cd frontend
                    npm run build
                '''
			}
		}

		// Docker 이미지 빌드
		stage('Docker Build') {
			steps {
				sh '''
                    docker compose build
                '''
			}
		}

		// 기존 컨테이너 종료 후 재배포
		stage('Deploy') {
			steps {
				sh '''
                    docker compose down || true
                    docker compose up -d
                '''
			}
		}

	}

	// 빌드 결과 처리
	post {

		success {
			echo '배포 완료'
		}

		failure {
			echo '배포 실패'
		}

		always {
			echo 'Pipeline 종료'
		}
	}
}