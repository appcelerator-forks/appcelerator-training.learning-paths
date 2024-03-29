theme:appcelerator-training
tableclass:striped
progress:true

# Filesystem

Appcelerator SDK Fundamentals

---cover

# Filesystem

## Appcelerator SDK Fundamentals

--- 

# In this lesson, you will:

- Explore Appcelerator Filesystem APIs
- Understand how and where to store data on the filesystem
- Understand LocalStorage for use with Mobile Web

--- 

# Files and the Filesystem
- Many Appcelerator APIs return Blob objects which point to binary data
- These blobs and other data (strings, commonly) can be written to Files
- The filesystem is the appropriate place to store binary data

--- 

# Filesystem Persistence and Security
- iOS/Android applications have limited Read/Write access to the filesystem
- Filesystem data persists until uninstall, except temp directories
- Filesystem locations are 'sandboxed' and private to your app
- Except external storage on Android
- Mobile Web has no filesystem access

--- 

# Common Storage Locations

- ```Ti.Filesystem.resourcesDirectory``` — read-only
- ```Ti.Filesystem.applicationDataDirectory``` — read/write
- ```Ti.Filesystem.tempDirectory``` — read/write
- ```Ti.Filesystem.applicationCacheDirectory``` — read/write

--- 

# iOS Filesystem

- ```applicationDirectory``` — read-only
- ```applicationSupportDirectory``` — read/write
- ```remoteBackup``` property

--- 

# Android Filesystem
- ```Ti.Filesystem.externalStorageDirectory``` — read/write, not sandboxed
- ```Ti.Filesystem.isExternalStoragePresent()``` — returns true/false
- ```resRawDirectory``` – Add files to platform/android/res/raw

--- 

# Filesystem Example

>![image001.png](../assets/tips/important.png) **WARNING:** In iOS 8, nativePath is relative to the the app container GUID, not the app bundle. It’s no longer absolute! 

```javascript
var file = Ti.Filesystem.getFile(Ti.Filesystem.resourcesDirectory, "myfile.txt"); 
var blob = file.read(); // binary representation of blob (file) 
var textOfFile = blob.text; 
var path = file.nativePath; // path to the file 
var mimetype = blob.mimeType; 
// dispose of file handle and blob 
file = null; 
blob = null; (no close() method) 
```

--- 

# Local Storage
- In-browser persistent storage location
- Support varies by browser and version
- Typical limit is **5MB** — for app, properties, Appcelerator libraries, etc.
- User can clear at any time via browser tools
- Local Storage == Resources directory in Mobile Web

--- 

# Scaffolding Example

![css float:left;width:40%;](assets/image5.png)

Persistence App: [http://github.com/appcelerator-training/Persistence](http://github.com/appcelerator-training/Persistence)

--- 

# Summary

In this lesson, you:

- Explored Appcelerator Filesystem APIs
- Examined how and where to store data on the filesystem
- Looked at LocalStorage for use with Mobile Web

---section

# Questions?