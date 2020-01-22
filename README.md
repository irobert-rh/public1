# public1


## Setup
* Jenkins + [ngrok](https://github.com/wernight/docker-ngrok)
```
# Launch Jenkins
docker run -it --name jenkins -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock --restart unless-stopped 4oh4/jenkins-docker
# Install Plugins
==> http://localhost:8080/pluginManager/available
==> "BlueOcean"(必须的UI) "CloudBee"(和Docker集成)

# Launch ngrok (Jenkins + Github-Webhook requirs public IP)
docker run --rm -it --link jenkins wernight/ngrok ngrok http jenkins:8080
   Web Interface                 http://0.0.0.0:4040
   Forwarding                    http://7324d8d3.ngrok.io -> http://jenkins:8080
   Forwarding                    https://7324d8d3.ngrok.io -> http://jenkins:8080
==> https://7324d8d3.ngrok.io is our public IP for Jenkins
```

* GitHub
  - Personal Access Token [url](https://github.com/settings/tokens)

* https://5534df42.ngrok.io/github-webhook/
