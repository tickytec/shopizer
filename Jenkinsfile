node {
   

    stage("configure") {
        sh "mkdir ${WORKSPACE}/${BUILD_NUMBER}/"
    }

    stage('run test'){
        sh "mkdir -p /tmp/reports"
        sh "cd /opt/homebrew/bin"
        sh "/opt/homebrew/bin/jmeter -n -t /Users/Mikita_Khatskevich/Jmeter/Shopizer2.0.jmx -l /tmp/reports/JMeter.jtl -e -o /tmp/reports/HtmlReport"
    }

    stage('publish results'){
        sh "mv /tmp/reports/* ${WORKSPACE}/${BUILD_NUMBER}/"
        archiveArtifacts artifacts: "${BUILD_NUMBER}/JMeter.jtl, ${BUILD_NUMBER}/HtmlReport/index.html"
    }
}
