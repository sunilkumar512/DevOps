pipeline {
 	agent {
 	  docker { image 'namrathanag21/fun:1' }
 	}
 	stages {
 	  stage('clone') {
 	    steps {
 	       
          git 'https://github.com/Namratha-16/cmake.git'
    	}
 	  }
 	   stage('build') {
 	    steps {
          sh 'cmake .'
    	}
 	  }
 stage ('Server'){
  steps {
   rtServer (
   id: "artifactory",
                 url: 'http://18.237.13.69:8082/artifactory',
                 username: 'admin',
                  password: 'Vardhan@49',
                  bypassProxy: true,
                   timeout: 300
                        )
         
           }
    } 
            
 stage('upload artifactory') {
  steps {
    rtUpload (
        serverId:"artifactory" ,
        spec: '''{
             "files": [
                     {
                      "pattern": "*.txt",
                      "target" : "result/"
                     }
                 ]
            }''',

       )
   }
 	 
 	 }
 	 }
 }
