# Reproducer 03808911

## Install Pipelines:
```
curl -s https://raw.githubusercontent.com/gmeghnag/03808911/main/Subscription.yaml | oc apply -f -
// wait for all the components to be installed
```

Run the reproducer:
```
oc apply -k https://github.com/gmeghnag/03808911
```