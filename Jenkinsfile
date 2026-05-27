node {
    def cbpArtifactId = registerBuildArtifactMetadata(
        name: "my-artifact",
        url: "https://example.com",
        version: "1.0.0.${BUILD_NUMBER}",
        componentId: "94c2d77a-658d-4fc0-9ae2-e65fdd4bf8ff"
    )
    echo "Registered artifact: $cbpArtifactId"

    sleep 5

    registerDeployedArtifactMetadata(
        artifactId: "$cbpArtifactId",
        targetEnvironment: "prod"
    )

    echo "Deploying"
    if (Math.random() < 0.5) {
        error "Deployment failed"
    }
    echo "Deployment succeeded"
}