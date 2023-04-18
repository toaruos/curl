After running autoreconf:

- Patch `config.sub` to add `toaru*` support.
- Patch `configure` to include libtool support for Toaru:
```
toaru*)
  version_type=linux # correct to gnu/linux during the next big refactor
  library_names_spec='$libname$release$shared_ext$versuffix $libname$release$shared_ext$major $libname$shared_ext'
  shlibpath_var=LD_LIBRARY_PATH
  shlibpath_overrides_runpath=yes
  ;;
```
- Configure with:
```
./configure --host=x86_64-pc-toaru --target=x86_64-pc-toaru --with-mbedtls=/home/klange/Projects/third-party/mbedtls-2.26.0 --disable-ipv6  --disable-unix-sockets --disable-threaded-resolver --disable-ntlm --disable-socketpair --with-ca-path=/usr/share/ca-certificates --enable-shared
```
- Install with:
```
cp -r lib/.libs/libcurl.so* ~/Projects/toaruos/base/usr/lib/ && cp src/.libs/curl ~/Projects/toaruos/base/usr/bin/
```


