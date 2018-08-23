node {
    checkout scm
    /* Docker pipeline plugin installed in Jenkins container */
    docker.image('gradle:latest').inside {
        stage('Build') {
            // commented lines for testing and inspection
            // sh 'gradle --version'
            // sh 'gradle tasks'
            // sh 'gradle projects'
            // sh 'pwd'
            // sh 'ls -la'
            sh 'gradle build -p /home/gradle/project'
        }
        stage('Test') {
            // TODO: replace with junit test running from built container
            // might move this to a later stage after building the container
            sh 'gradle --version'
        }
    }
}
node {
    stage('AppImageBuild') {
    sh 'pwd'
    sh 'ls -la'
    docker.build(
        'springboot',
        '--build-arg JAR_FILE=gs-spring-boot-docker-0.1.0.jar ./spring_boot_app')
    }

}