# Custom Resource Definition (CRD) Architecture Reference Manual

The `StellarNode` CRD defines additional columns shown by `kubectl get stellarnodes`. The table lists each column's type and the JSONPath used to read its value.

| Column | Type | JSONPath |
|---|---|---|
| Type | string | `.spec.nodeType` |
| Network | string | `.spec.network` |
| Ready | string | `.status.conditions[?(@.type=='Ready')].status` |
| Replicas | integer | `.spec.replicas` |
| Age | date | `.metadata.creationTimestamp` |

