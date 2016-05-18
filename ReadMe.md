## Fabric8 Jenkins Workflow Library

This git repository contains a library of reusable [Jenkins Workflows](https://github.com/jenkinsci/workflow-plugin) that can be used on a project.

<p align="center">
  <a href="http://fabric8.io/guide/cdelivery.html">
  	<img src="https://raw.githubusercontent.com/fabric8io/fabric8/master/docs/images/cover/cover_small.png" alt="fabric8 logo"/>
  </a>
</p>

The idea is to try promote sharing of workflows across projects where it makes sense.

You can then either

* reuse any of the flows as is
* fork this repository and make your own changes (hopefully submitting a Pull Request back)
* copy flows from this project into your own projects source code where you can modify it further

### Requirements

These flows make use of the [Fabric8 DevOps Workflow Steps](https://github.com/fabric8io/fabric8-jenkins-workflow-steps) which help when working with [Fabric8 DevOps](http://fabric8.io/guide/cdelivery.html) in particular for clean integration with the [Hubot chat bot](https://hubot.github.com/) and human approval of staging, promotion and releasing.

### Functions from the global library

#### Generic  

__TODO__

#### fabric8 release specific

These functions are focused specifically on the fabric8 release itself however could be used as examples or extended in users own setup.

##### deployRemoteOpenShift

Deploys the staged fabric8 release to a remote OpenShift cluster.  

NOTE: in order for images to be found by the the remote OpenShift instance it must be able to pull images from the staging docker registry.  Noting private networks and insecure-registry flags.

    node{
      deployRemoteOpenShift{
          url = 'test.fabric8.io'
          domain = 'staging.test.fabric8.io'
      }
    }

##### deployRemoteKubernetes

Deploys the staged fabric8 release to a remote Kubetnetes cluster.  

NOTE: in order for images to be found by the the remote OpenShift instance it must be able to pull images from the staging docker registry.  Noting private networks and insecure-registry flags.    

    node{
      deployRemoteKubernetes{
          url = 'https://kubernetes.fabric8.io'
          defaultNamespace = 'default'
      }
    }
