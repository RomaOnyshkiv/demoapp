### Yaml

| Name            | Prompt                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Description     | Example                                                    |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|------------------------------------------------------------|
| App             | kubectl ai "create pod with name app, and labels app:demo and app:run. Use this image - gcr.io/doki-417600/demo:v1.0.0 and set container with name - app and on port 8080 and port name http"                                                                                                                                                                                                                                                                                                                                                                                                           | Pode with app   | [app.yaml](../yaml/app.yaml)                               |
| Liveness probe  | kubectl ai "create pod with name app-livenessProbe and image gcr.io/doki-417600/demo:v1.0.0 with name app on namespace demo. Include livenessProbe with get request on port 8080 with path / and initial delay 5 and timeout minutes 3 and period minutes 10 and failure threshold 5. Containers works on 8088 and port name http"                                                                                                                                                                                                                                                                      | Liveness probe  | [app-livenessProbe,yaml](../yaml/app-livenessProbe.yaml)   |
| Readiness probe | kubectl ai "create pod with name app-readiness and image gcr.io/doki-417600/demo:v1.0.0 with name app. Include livenessProbe with get request on port 8080 with path / aand initial delay 5 and timeout minutes 3 and period minutes 10 and failure threshold 5. Containers works on 8080 and port name http. Also readinessProbe with path /ready with port 8080 and period minutes 2 and initial delay minutes 0 and failure treshold 3 and success treshold 1"                                                                                                                                       | Readiness probe | [app-reasinessProbe.yaml](../yaml/app-readinessProbe.yaml) |
| Volume mounts   | kubectl ai "create pod with name app-volume and gcr.io/doki-417600/demo:v1.0.0 with name app. Include livenessProbe with get request on port 8088 with path /healthy and initial delay 5 and timeout minutes 3 and period minutes 10 and failure threshold 5. Containers works on 8080 and port name http. Also readinessProbe with path /ready with port 8080 and period minutes 2 and initial delay minutes 0 and failure treshold 3 and success treshold 1. VolumeMounts with mount path /data and mount name data. Volumes with name data and host path /var/lib/app"                               | volume mount    | [app-volumeMounts.yaml](../yaml/app-volumeMounts.yaml)     |
| Cronjob         | kubectl ai "create cronjob with name app-cronjob and shedule every 15 minutes. Image bash command 'curl localhost:8080'. Restart policy on failure"                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Cronjob         | [app-cronjob.yaml](../yaml/app-cronjob.yaml)               |
| Job             | kubectl ai "create job with name app-job-rsync. Add volumes data-input and gcePersistentDisk with pdName glow-data-disk-200 and type - ext4. Container name init and image google/cloud-sdk:275.0.0-alpine and command /bin/sh, -c, gsutil -m rsync -dr gs://glow-sportradar/ /data/input andadd volume mounts name data-input and path /data/input. restart policy never .backoffLimit 0"                                                                                                                                                                                                              | Job             | [app-job.yaml](../yaml/app-job.yaml)                       |
| Multi container | kubectl ai "create pod with name app-multi-containers. Volumes name html. Container first name - 1st and image nginx with volumeMounts name html and path /usr/share/nginx/html. Next container name 2nd image debian and volumeMounts name html and path /html and command /bin/sh, -c and args where loop every second write date into /html/index.html"                                                                                                                                                                                                                                              | Multi container | [app-multicontainer](../yaml/app-multicontainer.yaml)      |
| Resources       | kubectl ai "create pod with name app-resource and image gcr.io/doki-417600/demo:v1.0.0 with name app. Include livenessProbe with get request on port 8088 with path /healthy and initial delay 5 and timeout minutes 3 and period minutes 10 and failure threshold 5. Containers works on 8080 and port name http. AContainers works on 8080 and port name http. Also readinessProbe with path /ready with port 8080 and period minutes 2 and initial delay minutes 0 and failure treshold 3 and success treshold 1. Add resources request cpu 100m and memory 128Mi, limits cpu 100m and memory 256Mi" | Resources       | [app-resources.yaml](../yaml/app-resources.yaml)           |
| Secret env      | kubectl ai "create pod with name app-secret-env. Container with name dokicontainer and image redis and env name SECRET_USERNAME where valueFrom secretKeyRef name dokisecret1 and key username, and second env name SECRET_PASSWORD with valueFrom secretKeyRef name dokisecret1 and key password. restart policy never"                                                                                                                                                                                                                                                                                | Secret env      | [pp-secret-env](../yaml/pp-secret-env)                     |
