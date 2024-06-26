# Shepherd scripts

## Use cases

### List shepherd leases

Available acitons:

- `RETURN`  - will select and target env using `shep_env`
- `CTRL-T` - will bump lease expiration time for 48 hours.

```sh
./shep_select
```

By default `shep_select` uses team's `tas-devex` namespace.
If you need custom namespace use `SH_NS` env variable.

```sh
SH_NS=official ./shep_select
```

### Target shepherd lease

This script will print key environment URLs and credentials. It will configure bosh, credhub, and cf cli with a dedicated config folder. You can target multiple leases in parallel terminal sessions. At this moment, this script depends on OpsManager and is not compatible with cf-deployment leases.

```sh
./shep_env
```

By default `shep_env` will use latest lease in `tas-devex` namespace.
This behavior could be customized via 
`SH_NS` - shepherd namespace and
`SH_ID` - shepherd lease id in the namespace above

```sh
SH_ID=${GUID:?Provide shepherd lease id} SH_NS=official ./shep_env
```
