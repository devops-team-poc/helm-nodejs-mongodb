# helm-nodejs-mongodb
MongoDB
1)  Create a disk file of 10GB named my-data-disk.
 #gcloud compute disks create --size=10GB  --zone=us-central1-c    my-data-disk
2)  Create PV of 1GB from the pd "my-data-disk".
3) Create PVC of equal or less size than the PV.
4)  Create deployment file for mongodb inside templates directory.
5) Use "fullname" template defined inside "_helpers.tpl" file.
6) Define the right mount path and storageName in "volumeMounts" section.
7) Define the name of PVC under persistentVolumeClaim inside volumes section.
8) Now define the service.yaml for mongodb , the labels and selector of it should match with the labels and selector of deployment.yaml of mongodb.
9) Now values.yaml file should be defined, inside which all the values of diferrent keys will be defined.
NodeJs
10) Create deployment.yaml file for Nodejs.
11) Create service.yaml file for Nodejs. Type should be loadBalancer and internal port(targetPort) will be 3000 and external port(port) will be 80.
12) Now values.yaml file should be defined, inside which all the values of diferrent keys will be defined.
13) Inside Chart.yaml of nodejs,  define dependencies of mongoDB chart.
14) Define local path where mongoDB chart is present in repository field and name field should match with the name of mongoDB chart name and version should match with verison of mongodb Chart.yaml version name.
15) Now run the following command to build dependency.
             #helm dependency build nodejs
16) Check if the dependency got build or not.
              # helm dependency list nodejs
17) In case of updating the helm dependency, run following command.
	   # helm dependency update nodejs
18) Now do the dry run of the above setup.
	    # helm install --dry-run node nodejs
19) After the dry-run gets successfully, do the actual helm install.
	    # helm install  node nodejs
20) To check if the desired resources got build successfully or not, run the following command.
	  # kubectl get po,pv,pvc,svc
21) Hit the endpoint or external IP of loadBalancer in web browser to check the proper running of application.
22) To uninstall the above deployment, run following.
	  helm uninstall node
			or
 	  helm del node
