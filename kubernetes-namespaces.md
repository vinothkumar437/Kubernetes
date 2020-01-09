<h2>Namespace is stuck in the Terminating state, how to delete it ?</h2>

<h3>Resolving the problem</h3>

<ol>
  <li>Run the following command to view the namespaces that are stuck in the Terminating state</li>
  <pre> kubectl get namespaces</pre>
  <li>Select a terminating namespace and view the contents of the namespace to find out the finalizer. Run the following command</li>
  <pre>kubectl get namespace "terminating-namespace" -o yaml</pre>
  <p>Your YAML contents might resemble the following output</p>
  <pre> apiVersion: v1
 kind: Namespace
 metadata:
   creationTimestamp: 2018-11-19T18:48:30Z
   deletionTimestamp: 2018-11-19T18:59:36Z
   name: <terminating-namespace>
   resourceVersion: "1385077"
   selfLink: /api/v1/namespaces/<terminating-namespace>
   uid: b50c9ea4-ec2b-11e8-a0be-fa163eeb47a5
 spec:
   finalizers:
   - kubernetes
 status:
   phase: Terminating</pre>
   <li>Run the following command to create a temporary JSON file</li>
   <pre>kubectl get namespace "terminating-namespace" -o json > tmp.json</pre>
   <li>Edit your tmp.json file. Remove the kubernetes value from the finalizers field and save the file</li>
   <p>Your tmp.json file might resemble the following output:</p>
   <pre>  {
      "apiVersion": "v1",
      "kind": "Namespace",
      "metadata": {
          "creationTimestamp": "2018-11-19T18:48:30Z",
          "deletionTimestamp": "2018-11-19T18:59:36Z",
          "name": "<terminating-namespace>",
          "resourceVersion": "1385077",
          "selfLink": "/api/v1/namespaces/<terminating-namespace>",
          "uid": "b50c9ea4-ec2b-11e8-a0be-fa163eeb47a5"
      },
      "spec": {
         "finalizers": 
      },
      "status": {
          "phase": "Terminating"
      }
  }</pre>
  <li>To set a temporary proxy IP and port, run the following command. Be sure to keep your terminal window open until you delete the stuck namespace</li>
  <pre> kubectl proxy</pre>
  <p>Your proxy IP and port might resemble the following output:</p>
  <pre> Starting to serve on 127.0.0.1:8001</pre>
</ol>
