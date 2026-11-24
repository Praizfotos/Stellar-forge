# Configuration Reference

Configuration options and references for Stellar-K8s.

The operator is configured at two levels: each Stellar deployment is described by a Kubernetes `StellarNode` custom resource, while Helm chart values configure the operator and its supporting components. The `StellarNode` `spec` contains node-specific settings such as node type, network, and role-specific configuration, with the CRD defining and validating the resource fields. Helm values configure installation-wide options and render settings into the operator deployment. Some runtime integrations also read environment variables directly; for example, `OTEL_EXPORTER_OTLP_ENDPOINT` sets the OpenTelemetry export endpoint.

Main places to configure Stellar-K8s:

- **`StellarNode` resources:** Set node-specific options in `spec`; the schema is defined in [`config/crd/stellarnode-crd.yaml`](../../config/crd/stellarnode-crd.yaml).
- **Environment variables:** Configure runtime integrations such as OpenTelemetry with `OTEL_EXPORTER_OTLP_ENDPOINT`.
- **Helm values:** Set operator and component options in [`charts/stellar-operator/values.yaml`](../../charts/stellar-operator/values.yaml), including `operator.logLevel` and `otel` settings.
