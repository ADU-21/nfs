# 如何配置nfs server
nfs-server(10.10.10.10):

```
vim /etc/export
/path/to/nfs 10.10.10.01(rw,sync,no_root_squash,no_subtree_check)
```

```
restart nfsserver
showmount -e
```

nfs-client(10.10.10.01)

```
vim /etc/fstab
10.10.10.10:/path/to/nfs  /mnt/nfs  nfs4 _netdev,auto 0 0 
```

```
mount -a
```

如果没有路由：

```
route 
vim /etc/sysconfig/network/routes
route add -host gw 
```