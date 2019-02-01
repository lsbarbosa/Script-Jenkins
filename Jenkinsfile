import groovy.json.JsonSlurper; 
    
try{ 
    List params = new ArrayList() 
    URL apiUrl = "https://github.com/lsbarbosa/MyProject.git".toURL() 
     List branches = new JsonSlurper().parse(apiUrl.newReader()) 
} 
catch(IOException ex){ 
    print ex 
} 
