gitExe = "serversGitbingit.exe"
currentBranch = ''
 
matcher = ~/* (.*)s/
 
process = "${gitExe} branch".execute()
process.in.eachLine{ 
     line -&gt; println line
     m = line =~ /*s+(.*)s?/
     if(m){     
          currentBranch = m[0][1] 
          return
     }
}
 
println "current: '$currentBranch'"
