# infrastructure-challenge
<h3>What i did in the Dockerfile</h3>
<p>As what was requested to make the dockerfile that build the image as light as possible , I made the dockerfile as more than one stage as build and run and this made the image more light <br>
==> you can run this file to build the image using this command : <b>docker build "image-name"</b></p>

<h3>What i did in the Jenkinsfile</h3>
<p>Coming to the pipeline , I tried to do it in a simple but effecient way to get the output i want which is an image pushed to the dockerhub but first and before every thing i made sure about putting the right credintials in jenkins as a platform or in the Jenkinsfile <br><br>
  ==> to start jenkins i used this command : <b>sudo systemctl enable jenkins</b> <br>
  ==> and to make sure jenkins can access docker.sock i used : <b>sudo usermod -aG docker jenkins</b> <br><br>
<img src="https://github.com/nabela-ashraf/infrastructure-challenge/assets/69801044/ab36a79a-2fc4-4990-9c4e-d3f07b58255a"><br>
<img src="https://github.com/nabela-ashraf/infrastructure-challenge/assets/69801044/574e4166-d106-469e-a115-a7f043d81362"><br>
</p>

<h3>What i did in the docker-compose file</h3>
<p>Coming to this part what i want to highlight that i tried to make sure that the application connects to the database by putting healthcheck in the database part so the application work in the way it should be <br>
==> to build the image and the necessary containers for the app to run : <b>docker-compose up</b><br>
==> if you want to deploy the application to a production environment use : <b>docker-compose build</b></p>

<h3>What i did in the helm chart</h3>
<p>i created the necessary file like the deployment files , service files , configmap , secret and PersistentVolumeClaim to make sure the database is always working .<br>
please check the folder named try to see the templates <br> 
==> to create the chart : <b>helm create "app-name"</b><br>
==> to install the chart : <b>helm install "realese-name" "chart-name"</b><br></p>
