kubectl apply -f gcp-premium.yaml
kubectl apply -f influxdb_svc.yaml
kubectl apply -f jmeter_influx_configmap.yaml
kubectl apply -f reporter.yaml
kubectl apply -f jslaves_svc.yaml
kubectl apply -f jslave.yaml
kubectl apply -f jmeter-master-configmap.yaml
kubectl apply -f jmaster.yaml
kubectl exec -ti influxdb_pod -- influx -execute 'CREATE DATABASE jmeter'
kubectl cp datasource.json influxdb_pod:/datasource.json
kubectl exec -ti influxdb_pod -- /bin/bash -c 'until [[ $(curl "http://admin:admin@localhost:3000/api/datasources" -X POST -H "Content-Type: application/json;charset=UTF-8" --data-binary @datasource.json) ]]; do sleep 5; done'
kubectl cp jmeterDash.json influxdb_pod:/jmeterDash.json
