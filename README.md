# kubectl.sh
A bunch of bash commands and scripts for kubectl operations

## top pods per node
```bash
pods=$(kubectl --context <context> get po -o wide --all-namespaces --field-selector spec.nodeName=<node_name> --no-headers| awk {'print $2,"--namespace "$1'})
echo $pods | while IFS= read -r line ; do kubectl --context <context> top pod $(echo $line) --no-headers; done
```
