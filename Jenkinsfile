podTemplate(label: 'pod-dromedary', 
    containers: [
        containerTemplate(
            name: 'dromedary',
            image: 'liatrio/lok-dromedary:0.1.0',
            ttyEnabled: true,
            command: 'cat'
        )
    ]){
    node ('pod-dromedary') {
      stage('Run dromedary'){
          git url: 'https://github.com/Liatrio-LOK/dromedary.git'
          container('dromedary') {
            sh("rm -rf node_modules/")
            sh("npm install")
            sh("npm install gulp gulp-util")
            sh("gulp test")
          }
      }
    }
    node ('master') {
    stage('build image'){
        sh("docker login 10.0.0.69:8082 -u Liatrio -p Test")
        sh("docker push 10.0.0.69:8082/docket:test")
    }
  }
}
