
/* CONFIGURATION END */

def repository_name = repository.replace("/", "%2F");
def api_branches = new URL("https://github.com/lsbarbosa/MyProject.git/" + repository_name).text

branches_list = new groovy.json.JsonSlurper().parseText(api_branches)

/* Get only branches with "release/" prefix */
def branchesMatch = "^release/.*"
def matched_branches = branches_list.findAll { it.name =~ /$branchesMatch/ }

def b = matched_branches.sort{ it.commit.committed_date }.reverse().take(5)

def results = (t << b).sort{ it.commit.committed_date }.reverse().flatten()

return results.name
