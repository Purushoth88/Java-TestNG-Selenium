node {
    // Mark the code checkout 'stage'....
    stage 'Checkout'
    // Get some code from a GitHub repository
    git url: 'https://github.com/Purushoth88/Java-TestNG-Selenium.git'
    stage 'Compile'
    sh 'mvn compile'
    stage 'Test'
    sauce('saucelabs') {
        sauceconnect(useGeneratedTunnelIdentifier: true, verboseLogging: true) {
            sh 'mvn test'
        }
    }
    stage 'Collect Results'
    step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
    step([$class: 'SauceOnDemandTestPublisher'])
}
