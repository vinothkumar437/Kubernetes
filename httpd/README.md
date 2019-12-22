<h3>Apache Deployment in Kubernetes with Nginx Ingress Controller</h3>

<ol>
  <li>Create the apache deployement</li>
  <pre>kubectl create -f httpd-deployment.yaml</pre>
  <li> Expose the service through command line or yaml </li>
  <b>command line</b>
  <pre>kubectl expose deploy httpd-deployment --port 80</pre>
  <p>or</p>
  <b>through yaml file</b>
  <pre>kubectl create -f httpd-service.yaml</pre>
  <li>create a ingress</li>
  <pre>kubectl create -f httpd-ingress.yaml</pre>
  <li>Get the routes</li>
  <pre>kubectl get ingress
NAME                       HOSTS                          ADDRESS   PORTS   AGE
httpd-deployment-ingress   apache.cloudapps.example.com             80      5s</pre>
</ol>
