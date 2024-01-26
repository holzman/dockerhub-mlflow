# mlflow docker image

This was taken and updated from https://hub.docker.com/r/evk02/mlflow


## Upgrade

When after a version upgrade the MLFlow container errors out, then check out the logs.
Frequently new versions require a database schema upgrade, so you need to call the new version with
the `db upgrade` SQLAlchemy command while pointing to the MySQL instance:
```
$ kubectl run  -i --tty --rm mlflow-upgrade --image={image} --restart=Never \
-- sh -c 'mlflow db upgrade [db uri]'
```

db uri should be something like ```postgresql://mlflow:[postgresql pw]@mlflow-postgresql:5432/mlflow```
