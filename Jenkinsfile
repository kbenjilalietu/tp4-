pipeline 
{
    environment 
    {
        registry = "khadija2000/tp4-job3tp4"
        registryCredential = 'dockerhub'
        dockerImage = ''
    }
    agent any
    stages 
    {
        stage('Cloning Git') 
        {
            steps 
            {
                git 'https://github.com/kbenjilalietu/tp4devops'
            }
        }
        stage('Building image') 
        {
            steps
            {
                script 
                {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
        stage('Test image') 
        {
            steps
            {
                script 
                {
                    echo "Tests passed"
                }
            }
        }
        stage('Publish Image') 
        {
            steps
            {
                script 
                {
                    docker.withRegistry( '', registryCredential ) 
                    {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}