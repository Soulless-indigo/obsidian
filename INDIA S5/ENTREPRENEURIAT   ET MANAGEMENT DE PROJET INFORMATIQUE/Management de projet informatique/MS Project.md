
**Step 1.0:** OPEN CMD AS ADMINISTRATOR 

**Step 1.1:** Open location of the Project/Visio installed on your PC.  
If you install it in the ProgramFiles folder, the path will be “%ProgramFiles%\Microsoft Office\Office16” or “%ProgramFiles(x86)%\Microsoft Office\Office16”. It depends on the architecture of the Windows OS you are using. If you are not sure of this issue, don’t worry, just run both of the commands above. One of them will be not executed and an error message will be printed on the screen.

```
cd /d %ProgramFiles(x86)%\Microsoft Office\Office16
cd /d %ProgramFiles%\Microsoft Office\Office16
```


**Step 1.2:** Convert your retail license to volume one.  
This step is required. You can not install the KMS client product key of Project/Visio without a volume license.

For Project 2021:

```
cscript ospp.vbs /inslic:"..\root\Licenses16\pkeyconfig-office.xrm-ms"&(for /f %x in ('dir /b ..\root\Licenses16\client-issuance*.xrm-ms') do cscript ospp.vbs /inslic:"..\root\Licenses16\%x")&(for /f %x in ('dir /b ..\root\Licenses16\projectprovl_kms*.xrm-ms') do cscript ospp.vbs /inslic:"..\root\Licenses16\%x")&(for /f %x in ('dir /b ..\root\Licenses16\projectpro2021vl_kms*.xrm-ms') do cscript ospp.vbs /inslic:"..\root\Licenses16\%x")
```


**Step 1.3:** Activate your Project/Visio using KMS client key  
Make sure your PC is connected to the internet, then run the following command. Do not forget to replace THE_CLIENT_KEY with the KMS client key of your product.

```
cscript ospp.vbs /inpkey:FTNWT-C6WBT-8HMGF-K9PRX-QV9H8
cscript ospp.vbs /sethst:e8.us.to
cscript ospp.vbs /setprt:1688
cscript ospp.vbs /act
```

![[Pasted image 20231023105628.png]]
