node {
    stage ("Checkout AuthService"){
        git branch: 'main', url: ' https://github.com/foxwas/bahmsdfox-msdauthservice'
    }
    
    stage ("Gradle Build - AuthService") {
        sh 'gradle clean build'
    }
    
    stage ("Gradle Bootjar-Package - AuthService") {
        sh 'gradle bootjar'
    }
    
    stage('User Acceptance Test - AuthService') {
	
	  def response= input message: 'Is this build good to go?',
	   parameters: [choice(choices: 'Yes\nNo', 
	   description: '', name: 'Pass')]
	
	  if(response=="Yes") {
	    stage('Release - AuthService') {
	      sh 'gradle build -x test'
	      sh 'echo AuthService is ready to release!'
	    }
	  }
    }
}
