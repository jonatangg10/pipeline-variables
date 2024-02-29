<p align="center">¡ Bienvenido !</p>
<p align="center"><b>Ejemplo practico de Jenkins</b></p>
<p align="center"><a>Dessarrollo un <b>Pipeline</b> para un proceso de manejo de variables del build</b></a></p>
<p align="center"><b>Si se puede inmaginar, se puede programar</b></p>

Ejecutado por el programador
Running as SYSTEM
Ejecutando en el nodo principalen el espacio de trabajo /var/jenkins_home/workspace/ejemplo-job-DSL
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/jenkins_home/workspace/ejemplo-job-DSL/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/jonatangg10/pipeline-variables.git # timeout=10
Fetching upstream changes from https://github.com/jonatangg10/pipeline-variables.git
 > git --version # timeout=10
 > git --version # 'git version 2.39.2'
 > git fetch --tags --force --progress -- https://github.com/jonatangg10/pipeline-variables.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse origin/main^{commit} # timeout=10
Checking out Revision f5bdf74f2e18e1b9261bf81a483c0040f9cf4731 (origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f f5bdf74f2e18e1b9261bf81a483c0040f9cf4731 # timeout=10
Commit message: "Update README.md"
 > git rev-list --no-walk f5bdf74f2e18e1b9261bf81a483c0040f9cf4731 # timeout=10
 > git tag -a -f -m Jenkins Build #12 jenkins-ejemplo-job-DSL-12 # timeout=10
FATAL: Could not apply tag jenkins-ejemplo-job-DSL-12
hudson.plugins.git.GitException: Command "git tag -a -f -m Jenkins Build #12 jenkins-ejemplo-job-DSL-12" returned status code 128:
stdout: 
stderr: Committer identity unknown

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'jenkins@53eb846526ea.(none)')

	at org.jenkinsci.plugins.gitclient.CliGitAPIImpl.launchCommandIn(CliGitAPIImpl.java:2842)
	at org.jenkinsci.plugins.gitclient.CliGitAPIImpl.launchCommandIn(CliGitAPIImpl.java:2762)
	at org.jenkinsci.plugins.gitclient.CliGitAPIImpl.launchCommandIn(CliGitAPIImpl.java:2757)
	at org.jenkinsci.plugins.gitclient.CliGitAPIImpl.launchCommand(CliGitAPIImpl.java:2051)
	at org.jenkinsci.plugins.gitclient.CliGitAPIImpl.launchCommand(CliGitAPIImpl.java:2063)
	at org.jenkinsci.plugins.gitclient.CliGitAPIImpl.tag(CliGitAPIImpl.java:1919)
Caused: hudson.plugins.git.GitException: Could not apply tag jenkins-ejemplo-job-DSL-12
	at org.jenkinsci.plugins.gitclient.CliGitAPIImpl.tag(CliGitAPIImpl.java:1921)
	at hudson.plugins.git.GitAPI.tag(GitAPI.java:354)
	at hudson.plugins.git.extensions.impl.PerBuildTag.onCheckoutCompleted(PerBuildTag.java:31)
	at hudson.plugins.git.GitSCM.checkout(GitSCM.java:1390)
	at hudson.scm.SCM.checkout(SCM.java:540)
	at hudson.model.AbstractProject.checkout(AbstractProject.java:1248)
	at hudson.model.AbstractBuild$AbstractBuildExecution.defaultCheckout(AbstractBuild.java:649)
	at jenkins.scm.SCMCheckoutStrategy.checkout(SCMCheckoutStrategy.java:85)
	at hudson.model.AbstractBuild$AbstractBuildExecution.run(AbstractBuild.java:521)
	at hudson.model.Run.execute(Run.java:1895)
	at hudson.model.FreeStyleBuild.run(FreeStyleBuild.java:44)
	at hudson.model.ResourceController.execute(ResourceController.java:101)
	at hudson.model.Executor.run(Executor.java:442)
Sending e-mails to: mariaeugenianieto345@gmail.com
[Slack Notifications] found #11 as previous completed, non-aborted build
[Slack Notifications] will send OnEveryFailureNotification because build matches and user preferences allow it
Finished: FAILURE
