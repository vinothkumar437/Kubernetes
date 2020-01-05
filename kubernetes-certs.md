<h3>Kubernetes Self Signed Certificate Generation for Dashboard</h3>
<ol>
<li>Create a directory on master node</li>
<pre>mkdir dashboard-certs</pre>
<pre>cd dashboard-certs/</pre>
  <li>Create a namespace</li>
  <pre>kubectl create namespace kubernetes-dashboard</pre>
  <li>Generate a key certificate</li>
  <pre>openssl genrsa -out dashboard.key 2048</pre>
  <li>Generate a csr from key </li>
  <pre>openssl req -days 36000 -new -out dashboard.csr -key dashboard.key -subj '/CN=dashboard-cert'</pre>
</ol>
