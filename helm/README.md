<h3>Helm Installation on the Kubernetes Cluster</h3>

<ol>
  <li>Download hel binaries from helm github releases page</li>
  <pre>https://github.com/helm/helm/releases</pre>
  <li>Move the helm file to /usr/local/bin/ </li>
  <pre>mv linux-amd64/helm /usr/local/bin/</pre>
  <li>Try to run some basic commands</li>
  <pre>helm version --short --client</pre>
  <pre>[admin@localhost ~]$ helm version --short --client
Client: v2.16.1+gbbdfe5e
[admin@localhost ~]$</pre>
  <li>Installing the Tiller</li>
  <p>Tiller is a companion to the helm command that runs on your cluster, receiving commands from helm and communicating directly with the Kubernetes API to do the actual work of creating and deleting resources.</p>
  <p>To give Tiller the permissions it needs to run on the cluster, we are going to make a Kubernetes serviceaccount resource.</p>
  <li>Create the tiller serviceaccount</li>
  <pre>kubectl -n kube-system create serviceaccount tiller</pre>
  <pre>[admin@localhost ~]$ kubectl -n kube-system create serviceaccount tiller
serviceaccount/tiller created
[admin@localhost ~]$</pre>
  <li>bind the tiller serviceaccount to the cluster-admin role</li>
  <pre>kubectl create clusterrolebinding tiller --clusterrole cluster-admin --serviceaccount=kube-system:tiller
clusterrolebinding.rbac.authorization.k8s.io/tiller created</pre>
  <li>Initialize the tiller through helm</li>
  <pre>[admin@local ~]$ helm init --service-account tiller  --skip-refresh
$HELM_HOME has been configured at /home/admin/.helm.

Tiller (the Helm server-side component) has been installed into your Kubernetes Cluster.

Please note: by default, Tiller is deployed with an insecure 'allow unauthenticated users' policy.
To prevent this, run `helm init` with the --tiller-tls-verify flag.For more information on
securing your installation see: https://docs.helm.sh/using_helm/#securing-your-helm-installation</pre>
<b>Note: Above Method is for disconnected environment</b>
<li>For connected environment</li>
<pre>[admin@local ~]$ helm init --service-account tiller 
$HELM_HOME has been configured at /home/admin/.helm.

Tiller (the Helm server-side component) has been installed into your Kubernetes Cluster.

Please note: by default, Tiller is deployed with an insecure 'allow unauthenticated users' policy.
To prevent this, run `helm init` with the --tiller-tls-verify flag.For more information on
securing your installation see: https://docs.helm.sh/using_helm/#securing-your-helm-installation
</pre>
</ol>
