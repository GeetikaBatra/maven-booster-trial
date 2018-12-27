#!/usr/bin/groovy
@Library('github.com/fabric8io/osio-pipeline@master')_

osio {

  config runtime: 'java', version: '1.8'

  ci {

    def app = processTemplate(params: [
          RELEASE_VERSION: "1.0.${env.BUILD_NUMBER}"
    ])
    
  }
  

  cd {

    def resources = processTemplate(params: [
          RELEASE_VERSION: "1.0.${env.BUILD_NUMBER}"
    ])
    
    build resources: resources

    deploy resources: resources, env: 'stage'

    deploy resources: resources, env: 'run', approval: 'manual'

  }
}
