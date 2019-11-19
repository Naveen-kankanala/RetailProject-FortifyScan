node (label: 'FortifySCA')
{
    
	  def ApplicationName 	    =	"Retail Project"
  	  def ApplicationVersion	=   "0.1"
  	  def bID		        	=	"RetailProject-FortifyScan"
	  def GitRepoURL	       	=	"https://github.com/vivek-venk/RetailJavaProject.git"
	  def FailureCriteria		=	"category: Path Manipulation"
	  def ResultsFile	    	=	"RetailProject.fpr"
	  
    stage('Git')
    {
        git GitRepoURL
    }
    stage('Fortify Clean')
    {
        fortifyClean addJVMOptions: '', buildID: bID, logFile: '', maxHeap: ''   
    }
    stage('Fortify Update')
    {
        fortifyUpdate proxyPassword: '', proxyURL: '', proxyUsername: '', updateServerURL: 'https://update.fortify.com'
    }
    stage('Fortify Translate')
    {
        fortifyTranslate addJVMOptions: '', buildID: bID, excludeList: '', logFile: '', maxHeap: '', projectScanType: fortifyJava(javaAddOptions: '', javaClasspath: '', javaSrcFiles: '**/*.java', javaVersion: '1.8')
    }
    stage('Fortify Scan')
    {
        fortifyScan addJVMOptions: '', addOptions: '', buildID: bID, customRulepacks: '', logFile: '', maxHeap: '', resultsFile: ResultsFile
    }  
     stage('Fortify Upload')
    {
        fortifyUpload appName: ApplicationName, appVersion: ApplicationVersion, failureCriteria: FailureCriteria, filterSet: '', pollingInterval: '1', resultsFile: ResultsFile
    }   
} 
