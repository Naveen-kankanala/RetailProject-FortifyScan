node
{
    stage('Git')
    {
        git 'https://github.com/vivek-venk/RetailJavaProject.git'
    }
    stage('Fortify Clean')
    {
     fortifyClean addJVMOptions: '', buildID: 'RetailProject-FortifyScan', logFile: '', maxHeap: ''   
    }
    stage('Fortify Update')
    {
        fortifyUpdate proxyPassword: '', proxyURL: '', proxyUsername: '', updateServerURL: 'https://update.fortify.com'
    }
    stage('Fortify Translate')
    {
        fortifyTranslate addJVMOptions: '', buildID: 'RetailProject-FortifyScan', excludeList: '', logFile: '', maxHeap: '', projectScanType: fortifyJava(javaAddOptions: '', javaClasspath: '', javaSrcFiles: '**/*.java', javaVersion: '1.8')
    }
    stage('Fortify Scan')
    {
        fortifyScan addJVMOptions: '', addOptions: '', buildID: 'RetailProject-FortifyScan', customRulepacks: '', logFile: '', maxHeap: '', resultsFile: 'RetailProject.fpr'
    }  
     stage('Fortify Upload')
    {
        fortifyUpload appName: 'Retail Project', appVersion: '0.1', failureCriteria: 'category: Path Manipulation', filterSet: '', pollingInterval: '1', resultsFile: 'RetailProject.fpr'
    }
    
} 
