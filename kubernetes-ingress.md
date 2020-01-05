<h3>Installing the Ingress Controller</h3>
  <p>Clone the github repository</p>
  <pre>[root@k8smaster ~]# git clone https://github.com/nginxinc/kubernetes-ingress.git
Cloning into 'kubernetes-ingress'...
remote: Enumerating objects: 20842, done.
remote: Total 20842 (delta 0), reused 0 (delta 0), pack-reused 20842
Receiving objects: 100% (20842/20842), 34.85 MiB | 6.39 MiB/s, done.
Resolving deltas: 100% (10341/10341), done.
[root@k8smaster ~]#</pre>
  <h3>Create a Namespace, a SA, the Default Secret, the Customization Config Map, and Custom Resource Definitions</h3>
  <ol>
  <li>Create a namespace and a service account for the Ingress controller</li>
  <pre>kubectl apply -f common/ns-and-sa.yaml</pre>
  <li>Create a secret with a TLS certificate and a key for the default server in NGINX</li>
  <pre>kubectl apply -f common/default-server-secret.yaml</pre>
  <li>Create a config map for customizing NGINX configuration</li>
  <pre>kubectl apply -f common/nginx-config.yaml</pre>
  <li>Create custom resource definitions for VirtualServer and VirtualServerRoute resources</li>
  <pre>kubectl apply -f common/custom-resource-definitions.yaml</pre>
  </ol>
