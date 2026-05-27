pipeline {
    agent any

//    environment {
//        IMAGE_TAG = "1.0.0"
//        IMAGE_DIGEST = "sha256:abc123"
//    }

    stages {
        stage('Register Artifacts') {
            steps {
                script {
                    def cbpArtifactId = registerBuildArtifactMetadata(
                            name: "my-artifact",
                            url: "https://example.com",
                            version: "1.0.0.${BUILD_NUMBER}",
                            label: "pan1"
                    )

//                    def artifactOutput = registerBuildArtifactMetadata(
//                            name: "jenkins-test-image",
//                            version: "${env.IMAGE_TAG}",
//                            type: "docker",
//                            url: "docker.io/pankajydev/jenkins-test-image:${env.IMAGE_TAG}",
//                            digest: "${env.IMAGE_DIGEST}",
//                            label: "pan1"
//                    )

                    echo "Registered artifact: $cbpArtifactId"

                    sleep 5

                    registerDeployedArtifactMetadata(
                            artifactId: "$cbpArtifactId",
                            targetEnvironment: "PAN"
                    )

//                    registerDeployedArtifactMetadata(
//                            artifactId: "${artifactOutput}",
//                            artifactUrl: "docker.io/pankajydev/jenkins-test-image:${env.IMAGE_TAG}",
//                            targetEnvironment: "PAN",
//                            labels: "pan1"
//                    )
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo "Deploying"
                    if (Math.random() < 0.5) {
                        error "Deployment failed"
                    }
                    echo "Deployment succeeded"
                }
            }
        }
    }
}