pipeline{
            agent any
            stages{
                    stage('--Front End--'){
                            steps{
                                    sh '''
                                            image="13.40.18.235:5000/frontend:build-$BUILD_NUMBER"
                                            docker build -t $image /var/lib/jenkins/workspace/$JOB_BASE_NAME/frontend
                                            docker push $image
                                            kubectl set image deployment/frontend frontend=$image
                                    '''
                            }
                    }  
                    stage('--Service1--'){
                            steps{
                                    sh '''
                                            image="13.40.18.235:5000/rand1:build-$BUILD_NUMBER"
                                            docker build -t $image /var/lib/jenkins/workspace/$JOB_BASE_NAME/randapp1
                                            docker push $image
                                            kubectl set image deployment/randapp1 randapp1=$image
                                    '''
                            }
                    }
                    stage('--Service2--'){
                            steps{
                                    sh '''
                                            image="13.40.18.235:5000/rand2:build-$BUILD_NUMBER"
                                            docker build -t $image /var/lib/jenkins/workspace/$JOB_BASE_NAME/randapp2
                                            docker push $image
                                            kubectl set image deployment/randapp2 randapp2=$image
                                    '''
                            }
                    }
                    stage('--Back End--'){
                            steps{
                                    sh '''
                                            image="13.40.18.235:5000/backend:build-$BUILD_NUMBER"
                                            docker build -t $image /var/lib/jenkins/workspace/$JOB_BASE_NAME/backend
                                            docker push $image
                                            kubectl set image deployment/backend backend=$image
                                    '''
                            }
                    }
            }
    }
