 pipeline{
   agent {
     kubernetes {
       yaml '''
         apiVersion: v1
         kind: Pod
         metadata:
           name: mypod
         spec:
           containers:
           - name: build-agent
             image: maven:alpine
             command: 
              - cat
             tty: true
         '''
        }
    }
  }
