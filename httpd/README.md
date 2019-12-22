<h3>Apache Deployment in Kubernetes with Nginx Ingress Controller</h3>

<ol>
  <li>Create the apache deployement</li>
  <pre>kubectl create -f httpd-deployment.yaml</pre>
  <li> Expose the service through command line or yaml </li>
  <b>command line</b>
  <pre>kubectl expose deploy httpd-deployment --port 80</pre>
</ol>
