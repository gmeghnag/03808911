# Reproducer 03808911

## Install Pipelines:
```
curl -s https://raw.githubusercontent.com/gmeghnag/03808911/main/Subscription.yaml | oc apply -f -
```
Then wait for all the components to be installed


## Create the needed resources for the reproducer:
```
oc apply -k https://github.com/gmeghnag/03808911
```

## Execute the reproducer:
```
cat << EOF | oc create -n pipelines-demo -f -
apiVersion: tekton.dev/v1beta1
kind: PipelineRun
metadata:
  namespace: pipelines-demo
  name: my-pipelinerun
spec:
  serviceAccountName: pipeline
  pipelineRef:
    name: my-pipeline
EOF
```
```
oc logs -n pipelines-demo $(oc get po -o name -n pipelines-demo -l tekton.dev/pipeline=my-pipeline)
```