podTemplate(label: 'pod-dromedary', 
    containers: [
        containerTemplate(
            name: 'dromedary',
            image: 'lok-dromedary',
            ttyEnabled: true,
            command: 'cat',
            ports: [portMapping(name: 'service', containerPort: 8080, hostPort: 18080)]
        )
    ]) {
    node ('pod-dromedary') {
      stage('Run dromedary'){
          container('dromedary') 
      }
    }
}
