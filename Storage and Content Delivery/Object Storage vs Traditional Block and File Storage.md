* Block storage operates at lower level-raw storage device level-manages data as fixed blocks
* File storage operates at higher level-operating system level-manages data as files and folder in a hierarchy.
* both closely associated with the server and OS that is using the storage
* S3 is different-object storage
* independent of server
* data is managed by API built on HTTP 
* S3 obj has data and metadata
* objects reside inside buckets
* each obj has unique user-specified key
* each bucket can hold unlimited objects
* flat folder structure no hierarchy
* can't have sub buckets within buckets
* you can `get` or `put` an object operating on the whole object
* can't mount, open an obj or run OS over it
* robust abstraction for file storage
* 