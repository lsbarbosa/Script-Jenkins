import jenkins.*
import jenkins.model.*
import hudson.*
import hudson.model.*
import org.eclipse.jgit.transport.RemoteConfig;
import org.eclipse.jgit.transport.URIish;

def build = Thread.currentThread().toString()
def regexp= ".+?/job/([^/]+)/.*"
def match = build  =~ regexp
def jobName = match[0][1]
def job = Jenkins.instance.getJob(jobName)
def workspace = job.lastBuild.workspace

for(project in Hudson.instance.items) {
  scm = job.scm;
  if (scm instanceof hudson.plugins.git.GitSCM) {
    for (RemoteConfig cfg : scm.getRepositories()) {
      for (URIish uri : cfg.getURIs()) {
        gitUri = uri
      }
    }
  }
}

def branchlist = ["/bin/bash", "-c", "git ls-remote --heads ${gitUri}"].execute() | ["/bin/bash", "-c", "cut -f2"].execute()
branchlist.waitFor()

return branchlist.in.text.readLines()
