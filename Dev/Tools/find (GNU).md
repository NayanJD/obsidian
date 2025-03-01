#linux 

#### 1. Find a single file by name

```bash
find / -name "Foo.txt" 2>/dev/null
```

#### 2. Find a single file by approximate name

```shell
find / -iname "*foo*txt" 2>/dev/null
```

#### 3. Find recursively in directories

```shell
find ~/Documents -ls
```


