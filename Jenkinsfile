pipeline {
    options {
        buildDiscarder(logRotator(numToKeepStr: '7',artifactNumToKeepStr: '5'))
    }
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh '''
                docker login lo-harbor.yyjzt.com -u push -p Push1234

                cd $WORKSPACE


                mvn package
                docker build -t lo-harbor.yyjzt.com/wotu/kkfileview-$BRANCH_NAME:1.0.$BUILD_NUMBER .



                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'

                echo ' update prod ....'




            }
        }
        stage('Clean') {
                    steps {
                        echo 'Clean..'
                        //sh '''docker rmi -f $(docker images --filter "dangling=true" -q --no-trunc);'''
                        //sh '''docker rmi -f $(docker images | grep wotu | grep -v v$BUILD_NUMBER | awk '!($3 in a){a[$3]=1;print $3}');'''
                    }
                }
    }
}
