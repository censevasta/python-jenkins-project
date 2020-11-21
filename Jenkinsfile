pipeline{
    agent any 
    stages{
        stage("compile"){
            agent{
                any {
                    image 'python:alpine'
                }
            }
            
            steps{
                withEnv(["Home=${env.WORKSPACE}"]) {
                    sh 'pip install -r requirements.txt'
                    sh 'python -m py_compile src/*.py'
                    stash(name: 'compilation_result', includes: 'src/*.py*')
                }
            }
        }
    }
}
