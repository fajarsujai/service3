pipeline {
    agent any

    stages{
        stage("Docker Build"){
            steps{
                script{
                    sh "docker build -t fajarsujai/service3:${GIT_COMMIT}  --build-arg PORT=3003 ."
                }
            }
        }


        stage("Docker Push"){
            steps{
                script{
                    sh "docker push fajarsujai/service3:${GIT_COMMIT}"
                }
            }
        }


        stage("Generate Tag"){
            steps{
                script{
                    sh "sh generatetag.sh ${GIT_COMMIT}"
                }
            }
        }


        stage("Deploy"){
            steps{
                script{
                    sh "helm upgrade service3 myhelm/myhelm -f values.yaml -n develop"
                }
            }
        }
    }
}