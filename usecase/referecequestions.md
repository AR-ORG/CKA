* Create a namespace called 'mynamespace' and a pod with image nginx called nginx on this namespace
* Create the pod that was just described using YAML
* Create a busybox pod (using kubectl command) that runs the command "env". Run it and see the output
* Create a busybox pod (using YAML) that runs the command "env". Run it and see the output
* Get the YAML for a new namespace called 'myns' without creating it
* Get the YAML for a new ResourceQuota called 'myrq' without creating it
* Get pods on all namespaces
* Create a pod with image nginx called nginx and allow traffic on port 80
* Change pod's image to nginx:1.7.1. Observe that the pod will be killed and recreated as soon as the image gets pulled
* Get the pod's ip, use a temp busybox image to wget its '/'
* Get this pod's YAML without cluster specific information
* Get information about the pod, including details about potential issues (e.g. pod hasn't started)
* Get pod logs
* If pod crashed and restarted, get logs about the previous instance
* Connect to the nginx pod
* Create a busybox pod that echoes 'hello world' and then exits
* Do the same, but have the pod deleted automatically when it's completed
* Create an nginx pod and set an env value as 'var1=val1'. Check the env value existence within the pod
* Create a Pod with two containers, both with image busybox and command "echo hello; sleep 3600". Connect to the second container and run 'ls'
* Create 3 pods with names nginx1,nginx2,nginx3. All of them should have the label app=v1
* Show all labels of the pods
* Change the labels of pod 'nginx2' to be app=v2
* Get the label 'app' for the pods
* Get only the 'app=v2' pods
* Remove the 'app' label from the pods we created before
* Create a pod that will be deployed to a Node that has the label 'accelerator=nvidia-tesla-p100'
* Annotate pods nginx1, nginx2, nginx3 with "description='my description'" value
* Check the annotations for pod nginx1
* Remove the annotations for these three pods
* Remove these pods to have a clean state in your cluster
* Create a deployment with image nginx:1.7.8, called nginx, having 2 replicas, defining port 80 as the port that this container exposes (don't create a service for this deployment)
* View the YAML of this deployment
* View the YAML of the replica set that was created by this deployment
* Get the YAML for one of the pods
* Check how the deployment rollout is going
* Update the nginx image to nginx:1.7.9
* Check the rollout history and confirm that the replicas are OK
* Undo the latest rollout and verify that new pods have the old image (nginx:1.7.8)
* Do an on purpose update of the deployment with a wrong image nginx:1.91
* Verify that something's wrong with the rollout
* Return the deployment to the second revision (number 2) and verify the image is nginx:1.7.9
* Check the details of the third revision (number 3)
* Scale the deployment to 5 replicas
* Autoscale the deployment, pods between 5 and 10, targetting CPU utilization at 80%
* Pause the rollout of the deployment
* Update the image to nginx:1.9.1 and check that there's nothing going on, since we paused the rollout
* Resume the rollout and check that the nginx:1.9.1 image has been applied
* Delete the deployment and the horizontal pod autoscaler you created
* Create a job with image perl that runs default command with arguments "perl -Mbignum=bpi -wle 'print bpi(2000)'"
* Wait till it's done, get the output
* Create a job with the image busybox that executes the command 'echo hello;sleep 30;echo world'
* Follow the logs for the pod (you'll wait for 30 seconds)
* See the status of the job, describe it and see the logs
* Delete the job
* Create the same job, make it run 5 times, one after the other. Verify its status and delete it
* Create the same job, but make it run 5 parallel times
* Create a cron job with image busybox that runs on a schedule of "*/1 * * * *" and writes 'date; echo Hello from the Kubernetes cluster' to standard output
* See its logs and delete it
* Create a configmap named config with values foo=lala,foo2=lolo
* Display its values
* Create and display a configmap from a file
* Create and display a configmap from a .env file
* Create and display a configmap from a file, giving the key 'special'
* Create a configMap called 'options' with the value var5=val5. Create a new nginx pod that loads the value from variable 'var5' in an env variable called 'option'
* Create a configMap 'anotherone' with values 'var6=val6', 'var7=val7'. Load this configMap as env variables into a new nginx pod
* Create a configMap 'cmvolume' with values 'var8=val8', 'var9=val9'. Load this as a volume inside an nginx pod on path '/etc/lala'. Create the pod and 'ls' into the '/etc/lala' directory.
* Create the YAML for an nginx pod that runs with the UID 101. No need to create the pod
* Create the YAML for an nginx pod that has the capabilities "NET_ADMIN", "SYS_TIME" added on its single container
* Create an nginx pod with requests cpu=100m,memory=256Mi and limits cpu=200m,memory=512Mi
* Create a secret called mysecret with the values password=mypass
* Create a secret called mysecret2 that gets key/value from a file
* Get the value of mysecret2
* Create an nginx pod that mounts the secret mysecret2 in a volume on path /etc/foo
* Delete the pod you just created and mount the variable 'username' from secret mysecret2 onto a new nginx pod in env variable called 'USERNAME'
* See all the service accounts of the cluster in all namespaces
* Create a new serviceaccount called 'myuser'
* Create an nginx pod that uses 'myuser' as a service account
* Create an nginx pod with a liveness probe that just runs the command 'ls'. Save its YAML in pod.yaml. Run it, check its probe status, delete it.
* Modify the pod.yaml file so that liveness probe starts kicking in after 5 seconds whereas the period of probing would be 10 seconds. Run it, check the probe, delete it.
* Create an nginx pod (that includes port 80) with an HTTP readinessProbe on path '/' on port 80. Again, run it, check the readinessProbe, delete it.
* Create a busybox pod that runs 'i=0; while true; do echo "$i: $(date)"; i=$((i+1)); sleep 1; done'. Check its logs
* Create a busybox pod that runs 'ls /notexist'. Determine if there's an error (of course there is), see it. In the end, delete the pod
* Create a busybox pod that runs 'notexist'. Determine if there's an error (of course there is), see it. In the end, delete the pod forcefully with a 0 grace period
* Get CPU/memory utilization for nodes ([metrics-server](https://github.com/kubernetes-incubator/metrics-server) must be running)
* Create a pod with image nginx called nginx and expose its port 80
* Confirm that ClusterIP has been created. Also check endpoints
* Get pod's ClusterIP, create a temp busybox pod and 'hit' that IP with wget
* Convert the ClusterIP to NodePort and find the NodePort port. Hit it using Node's IP. Delete the service and the pod
* Create a deployment called foo using image 'dgkanatsios/simpleapp' (a simple server that returns hostname) and 3 replicas. Label it as 'app=foo'. Declare that containers in this pod will accept traffic on port 8080 (do NOT create a service yet)
* Get the pod IPs. Create a temp busybox pod and trying hitting them on port 8080
* Create a service that exposes the deployment on port 6262. Verify its existence, check the endpoints
* Create a temp busybox pod and connect via wget to foo service. Verify that each time there's a different hostname returned. Delete deployment and services to cleanup the cluster
* Create an nginx deployment of 2 replicas, expose it via a ClusterIP service on port 80. Create a NetworkPolicy so that only pods with labels 'access: true' can access the deployment and apply it
* Create busybox pod with two containers, each one will have the image busybox and will run the 'sleep 3600' command. Make both containers mount an emptyDir at '/etc/foo'. Connect to the second busybox, write the first column of '/etc/passwd' file to '/etc/foo/passwd'. Connect to the first busybox and write '/etc/foo/passwd' file to standard output. Delete pod.
* Create a PersistentVolume of 10Gi, called 'myvolume'. Make it have accessMode of 'ReadWriteOnce' and 'ReadWriteMany', storageClassName 'normal', mounted on hostPath '/etc/foo'. Save it on pv.yaml, add it to the cluster. Show the PersistentVolumes that exist on the cluster
* Create a PersistentVolumeClaim for this storage class, called mypvc, a request of 4Gi and an accessMode of ReadWriteOnce and save it on pvc.yaml. Create it on the cluster. Show the PersistentVolumeClaims of the cluster. Show the PersistentVolumes of the cluster
* Create a busybox pod with command 'sleep 3600', save it on pod.yaml. Mount the PersistentVolumeClaim to '/etc/foo'. Connect to the 'busybox' pod, and copy the '/etc/passwd' file to '/etc/foo/passwd'
* Create a second pod which is identical with the one you just created (you can easily do it by changing the 'name' property on pod.yaml). Connect to it and verify that '/etc/foo' contains the 'passwd' file. Delete pods to cleanup
* Create a busybox pod with 'sleep 3600' as arguments. Copy '/etc/passwd' from the pod to your local folder
