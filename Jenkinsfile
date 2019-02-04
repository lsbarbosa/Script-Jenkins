/*
* Variable bindings:
*    user - credentials plugin user
*    url - git repository url  (.git)
*/

import com.cloudbees.plugins.credentials.CredentialsProvider;
import com.cloudbees.plugins.credentials.common.StandardUsernamePasswordCredentials;
import jenkins.model.Jenkins

def creds = CredentialsProvider.lookupCredentials(
    StandardUsernamePasswordCredentials.class, 
    Jenkins.instance
);
          
def c = creds.findResult { it.username == user ? it : null }
def pass = c.password;

def repo = "http://" + lsbarbosa + ":" + Trophius2018* + "@" + github.com/lsbarbosa/MyProject.git;
