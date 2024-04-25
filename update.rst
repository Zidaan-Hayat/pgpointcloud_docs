pgPointcloud extension
=========

Once a new version of pgPointcloud installed, you may want to update your
databases where the extension is already in use. The first thing to compare is
the version currently used with versions actually available on your system:

``` sql
   SELECT pc_version();
   --> 1.1.1

   SELECT version FROM pg_available_extension_versions WHERE name ='pointcloud';
   --> 1.1.1
   --> 1.2.1
```

Then you can update to the latest version:

``` sql
   ALTER EXTENSION pointcloud;
   ALTER EXTENSION pointcloud_postgis;
```

``` sql
   ALTER EXTENSION pointcloud UPDATE TO '1.2.1';

   SELECT pc_version();
   --> 1.2.1
```

> [!WARNING]
> The GHT compression has been removed in the 1.2.0 version. Unfortunately,
> you have to remove the compression on your tables before updating the
> extension from 1.1.x to a higher version. Some information are available in
> the `Schema and compression`_ tutorial.