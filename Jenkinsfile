podTemplate(label: 'pod-dromedary', 
    containers: [
        containerTemplate(
            name: 'dromedary',
            image: 'liatrio/lok-dromedary:0.1.0',
            ttyEnabled: true,
            command: 'cat',
            ports: [portMapping(name: 'service', containerPort: 8080, hostPort: 18080)]
        )
    ]) {
    node ('pod-dromedary') {
      stage('Run dromedary'){
        git url: 'https://github.com/Liatrio-LOK/dromedary.git', branch: 'LOK-31-minimal-pipeline'
          container('dromedary') {
            sh("npm install gulp -g")
            sh("gulp")
          }
      }
    }
}
