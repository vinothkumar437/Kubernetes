<h3>Helm Installation on the Kubernetes Cluster</h3>

<ol>
  <li>Download hel binaries from helm github releases page</li>
  <pre>https://github.com/helm/helm/releases</pre>
  <li>Move the helm file to /usr/local/bin/ </li>
  <pre>mv linux-amd64/helm /usr/local/bin/</pre>
  <li>Try to run some basic commands</li>
  <pre>helm version --short --client</pre>
  <pre>[admin@localhost ~]$ helm version --short --client
v3.0.2+g19e47ee
[admin@localhost ~]$</pre>
</ol>
