# librassh
An interactive file explorer for secure storage via ssh

Presently a speculative prototype project, but I thought I'd build something to allow me to drag and drop files into a remote server and maybe play with a GUI wrapped around ZFS's snapshot feature to reflect a versioned file system.

Something like a DIY dropbox, in the interest of making it easy to operate your own infrastructure.
Libras3 should have an identical API for S3 storage so library interfaces would work equivalently. 

So it's gonna work like, the client POSTs to a shell script that reads the file body on STDIN. The args might include username/password/filename/file-crypto-password/compression-algo/crypto-algo, and could fall back to defaults or environment variables.

So if I successfully log in to my server as root, my server can read these configurations from a file only readably by root, so I can just get straight to moving files around. Any time I create or modify a file, the body gets compressed, encrypted, and scp'd to remote storage. Or my own hardware. So that might allow me to use those $5/month cloud servers that only have a 20GB disk or something and use that as my front end to terascale, local storage, not keeping my data up in the sky. So there's that RAIN concept. When I'm at home, the files I created are sitting safe and sound. When I'm out, I can still pull the files off my home storage, with my cloud server piping from scp to client. 

So it remains to be seen what kind of performance hit it takes to open text files out from scp. There's surely some amount of overhead for that ssh handshake and some power spent decrypting. We'll see if its worth it. It's just an option.

Hopefully I can make it clear what kind of libary your looking at. Maybe even just a subtle label in the background "ZFS/HDFS+/S3/SCP+ZFS" something like that. Would be espcially cool if it was intuitive to drag a file from a librassh block to a libras3 block to get a public facing link, or drag to and from a local disk for easy archival.
