# NFS server 
Allows for many read write connections in your cluster.

`helm install $RELEASE ./nfs-server/`

## Zero to jupyterhub

```yaml
singleuser:
  storage:
    extraVolumes:
      - name: jupyterhub-shared
        persistentVolumeClaim:
          claimName: {$RELEASE}-nfs-server
    extraVolumeMounts:
      - name: jupyterhub-shared
        mountPath: /home/jovyan/shared
```

As you only have `jovyan` user in Jupyterhub you need to create a folder that has `777` rights.

