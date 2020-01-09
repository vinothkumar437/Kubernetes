<h2>Namespace is stuck in the Terminating state, how to delete it ?</h2>

<h3>Resolving the problem</h3>

<ol>
  <li>Run the following command to view the namespaces that are stuck in the Terminating state</li>
  <pre> kubectl get namespaces</pre>
  <li>Select a terminating namespace and view the contents of the namespace to find out the finalizer. Run the following command</li>
  <pre>kubectl get namespace "terminating-namespace" -o yaml</pre>
</ol>
