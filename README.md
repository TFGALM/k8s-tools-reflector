# Reflector

Se utiliza para mantener sincronizados en memoria los recursos del clúster observando cambios en tiempo real desde la API.

## Instalación

> **DOCUMENTACIÓN OFICIAL**: [Documentación](https://github.com/emberstack/kubernetes-reflector/tree/main)

La instalación de Reflector la haremos usando el helm oficial de Reflector

```bash
helm repo add emberstack https://emberstack.github.io/helm-charts
helm repo update
helm -n reflector  upgrade --install reflector emberstack/reflector --create-namespace -f values.default.yaml
```

Se debe agregar los siguientes **annotations** para que los secrets o los configMap
repliquen en todos los namespace:

```yaml
annotations:
  reflector.v1.k8s.emberstack.com/reflection-allowed: "true"
  reflector.v1.k8s.emberstack.com/reflection-auto-enabled: "true"
```
