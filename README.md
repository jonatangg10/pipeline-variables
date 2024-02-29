<p align="center">¡ Bienvenido !</p>
<p align="center"><b>Ejemplo practico de Jenkins</b></p>
<p align="center"><a>Dessarrollo un <b>Pipeline</b> para un proceso de manejo de variables del build</b></a></p>
<p align="center"><b>Si se puede inmaginar, se puede programar</b></p>

job('ejemplo-job-DSL') {
  	description('Job DSL de ejemplo para el curso de Jenkins')
  	scm {
    	git('https://github.com/jonatangg10/pipeline-variables.git', 'main') { node ->
      		node / gitConfigName('jonatangg10')
      		node / gitConfigName('mariaeugenianieto345@gmail.com')
  		}
     	parameters {
    		stringParam('nombre', defaultValue = 'Jonatan', description = 'Parametro de cadena para el Job Booleano')
    		choiceParam('planeta', ['Mercurio', 'Venus', 'Tierrra', 'Marte', 'Jupiter', 'Saturno', 'Urano', 'Neptuno'])
    		booleanParam('agente', false)
  		}
      	triggers {
    		cron('H/7 * * * *')
  		}
      	steps {
    		shell("bash jobscript.sh")
  		}
		 publishers {
    		mailer('mariaeugenianieto345@gmail.com', true, true)
    			slackNotifier {
      				notifyAborted(true)
      				notifyEveryFailure(true)
      				notifyNotBuilt(false)
      				notifyUnstable(false)
      				notifyBackToNormal(true)
      				notifySuccess(false)
      				notifyRepeatedFailure(false)
      				startNotification(false)
      				includeTestSummary(false)
      				includeCustomMessage(false)
      				customMessage(null)
      				sendAs(null)
      				commitInfoChoice('NONE')
      				teamDomain(null)
      				authToken(null)
    			}
  			}
	}
}
