# builds-pods-storage-collector

```
oc apply -k https://github.com/gmeghnag/builds-pods-storage-collector.git
```
```
oc logs -n builds-pods-storage-collector $(oc get po -l app=builds-pods-storage-collector -n builds-pods-storage-collector -o jsonpath='{.items[0].metadata.name}') -f | jq
```

## Expected output
```
{
  "DateTimeUTC": "2023-07-25T12:16:59Z",
  "Node": "ip-10-0-129-153.eu-central-1.compute.internal",
  "Namespace": "default",
  "PodName": "builds-pods-storage-collector-1-build",
  "UsedGB": "20.018962860107422"
}
{
  "DateTimeUTC": "2023-07-25T12:17:20Z",
  "Node": "ip-10-0-129-153.eu-central-1.compute.internal",
  "Namespace": "default",
  "PodName": "builds-pods-storage-collector-1-build",
  "UsedGB": "20.018962860107422"
}
..
```

## How to test
```
curl -sk https://raw.githubusercontent.com/gmeghnag/builds-pods-storage-collector/main/Dockerfile | oc new-build -n default --to=builds-pods-storage-collector -D  -
```

