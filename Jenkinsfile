import groovy.json.JsonSlurper; 
try{ 
    List<String>params = new ArrayList<String>() 
    URL apiUrl = "https://github.com/lsbarbosa/MyProject".toURL() 
    List branches = new JsonSlurper().parse(apiUrl.newReader()) 
    for (branch in branches) { 
    params.add(branch.name) 
    } 
    return params 
} 
catch(IOException ex){ 
    print ex 
} 
