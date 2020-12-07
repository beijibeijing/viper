
### NEW Watching and re-reading config files

use github.com/radovskyb/watcher to Watching and re-reading config files,so it could work in k8s.

```go
viper.WatcherConfig()
viper.OnWatcherConfigChange(func(e watcher.Event) {
	fmt.Println("Config file changed:", e.FileInfo)
})
```

### Old Watching and re-reading config files

Viper supports the ability to have your application live read a config file while running.

Gone are the days of needing to restart a server to have a config take effect,
viper powered applications can read an update to a config file while running and
not miss a beat.

Simply tell the viper instance to watchConfig.
Optionally you can provide a function for Viper to run each time a change occurs.

**Make sure you add all of the configPaths prior to calling `WatchConfig()`**

```go
viper.WatchConfig()
viper.OnConfigChange(func(e fsnotify.Event) {
	fmt.Println("Config file changed:", e.Name)
})
```