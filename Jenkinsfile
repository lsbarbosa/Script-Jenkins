import groovy.json.JsonSlurper;
try{
   List<String>params = new ArrayList<String>()
   URL apiUrl = "https://api.github.com/users/<repo-owner>/repos?access_token=<github-access-token>".toURL()
   List branches = new JsonSlurper().parse(apiUrl.newReader())
   for (branch in branches ) { 
     params.add(branch.name) 
   }
   return params
}
catch(IOException ex){
   print ex
}
