# win_container

```

docker run -dt --rm -v "C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\IDE\Remote Debugger:C:\remote_debugger:ro" -v "C:\Users\dyang\source\repos\ConsumingWCFService\ConsumingWCFService:C:\inetpub\wwwroot" -e "DEV_ENVIRONMENT=1" -e "VBCSCOMPILER_TTL=604800" -e "COMPLUS_ForceENC=1" -p 8080:80 --name web --entrypoint cmd consumingwcfservice:dev /c "start /B C:\ServiceMonitor.exe w3svc & C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus /noclrwarn /nosecuritywarn /nofirewallwarn /nowowwarn /fallbackloadremotemanagedpdbs /timeout:2147483646" 

```

```
docker exec web cmd /c "C:\Windows\System32\inetsrv\appcmd.exe set config -section:system.applicationHost/applicationPools /[name='DefaultAppPool'].processModel.identityType:LocalSystem /commit:apphost & C:\Windows\System32\inetsrv\appcmd.exe set config -section:system.webServer/security/authentication/anonymousAuthentication /userName: /commit:apphost"
```
