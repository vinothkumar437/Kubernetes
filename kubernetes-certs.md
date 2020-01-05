<h3>Kubernetes Self Signed Certificate Generation for Dashboard</h3>
<ol>
<li>Create a directory on master node</li>
<pre>mkdir dashboard-certs</pre>
<pre>cd dashboard-certs/</pre>
  <li>Create a namespace</li>
  <pre>kubectl create namespace kubernetes-dashboard</pre>
  <li>generate a key certificate</li>
  <pre>openssl genrsa -out dashboard.key 2048</pre>
</ol>
