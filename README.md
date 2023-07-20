# Visual Studio Remote Code Execution Vulnerability

- [Environment](#environment)
	- [OS](#os)
	- [Visual Studio Version](#visual-studio-version)
	- [Target](#target)
- [devenv.exe Functional analysis](#devenvexe-functional-analysis)
- [Vulnerable 1. Arbitrary Code Execution](#vulnerable-1-arbitrary-code-execution)
- [Case 1. Git clone repo and execute](#git-clone-repo-and-execute)


## environment
### OS
- Windows 11(x64) 22h2 22621.1992

### Visual Studio Version
- Visual Studio Community 2022 Version 17.6.5


### Target
- devenv.exe: You can build, debug, and deploy the Visual Studio project .sin file from the command line to set various options for IDE.
	- C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\IDE\devenv.exe
	- Version 17.6.5
## devenv.exe Functional analysis
#### details
- When a typical user double-clicks .sin, the command is executed and ide is executed as follows.
	- "C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\IDE\devenv.exe" "C:\Users\user\Downloads\poc\Crassus.sln"


## vulnerable 1. Arbitrary Code Execution

 Users can execute attacker code when attempting to log in to GitHub from an infected project.

### details


- Microsoft.VisualStudio.Interop.ni.dll

  

  ```
  21	SHELL32.dll	ShellExecuteExW + 0x7a	0x7ffa7d4e604a	C:\WINDOWS\System32\SHELL32.dll
  22	SHELL32.dll	ShellExecuteW + 0x81	0x7ffa7d4e6151	C:\WINDOWS\System32\SHELL32.dll
  23	msenv.dll	VStudioComposeMEF + 0x402a7f	0x7ffa49adcb8f	C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\IDE\msenv.dll
  24	Microsoft.VisualStudio.Interop.ni.dll	Microsoft.VisualStudio.Interop.ni.dll + 0x8103ae	0x7ffa39b403ae	C:\WINDOWS\assembly\NativeImages_v4.0.30319_64\Microsoft.V350b316e#\281f80b1e2fb8a57340c6bdbc2315afc\Microsoft.VisualStudio.Interop.ni.dll
  25	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll + 0x77032	0x7ff9ea1e7032	C:\Windows\assembly\NativeImages_v4.0.30319_64\Microsoft.Df9554d34#\adb584aa9539bc53ef0083153fdda492\Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll
  26	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll + 0x67b89	0x7ff9ea1d7b89	C:\Windows\assembly\NativeImages_v4.0.30319_64\Microsoft.Df9554d34#\adb584aa9539bc53ef0083153fdda492\Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll
  27	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll + 0x6515c	0x7ff9ea1d515c	C:\Windows\assembly\NativeImages_v4.0.30319_64\Microsoft.Df9554d34#\adb584aa9539bc53ef0083153fdda492\Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll
  28	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll + 0x765c5	0x7ff9ea1e65c5	C:\Windows\assembly\NativeImages_v4.0.30319_64\Microsoft.Df9554d34#\adb584aa9539bc53ef0083153fdda492\Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll
  29	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll + 0x67522	0x7ff9ea1d7522	C:\Windows\assembly\NativeImages_v4.0.30319_64\Microsoft.Df9554d34#\adb584aa9539bc53ef0083153fdda492\Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll
  30	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll + 0x64ee1	0x7ff9ea1d4ee1	C:\Windows\assembly\NativeImages_v4.0.30319_64\Microsoft.Df9554d34#\adb584aa9539bc53ef0083153fdda492\Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll
  31	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll + 0x6ba6b	0x7ff9ea1dba6b	C:\Windows\assembly\NativeImages_v4.0.30319_64\Microsoft.Df9554d34#\adb584aa9539bc53ef0083153fdda492\Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll
  32	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll + 0x7848a	0x7ff9ea1e848a	C:\Windows\assembly\NativeImages_v4.0.30319_64\Microsoft.Df9554d34#\adb584aa9539bc53ef0083153fdda492\Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll
  33	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll + 0x67312	0x7ff9ea1d7312	C:\Windows\assembly\NativeImages_v4.0.30319_64\Microsoft.Df9554d34#\adb584aa9539bc53ef0083153fdda492\Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll
  34	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll	Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll + 0x6a4c9	0x7ff9ea1da4c9	C:\Windows\assembly\NativeImages_v4.0.30319_64\Microsoft.Df9554d34#\adb584aa9539bc53ef0083153fdda492\Microsoft.Developer.IdentityService.GitHubProvider.UI.ni.dll
  35	Microsoft.Developer.IdentityService.Client.ni.dll	Microsoft.Developer.IdentityService.Client.ni.dll + 0x12db2b	0x7ff9ec97db2b	C:\WINDOWS\assembly\NativeImages_v4.0.30319_64\Microsoft.D487c049b#\17aa6534ea5939f3df10e1f242a027a9\Microsoft.Developer.IdentityService.Client.ni.dll
  36	Microsoft.Developer.IdentityService.Client.ni.dll	Microsoft.Developer.IdentityService.Client.ni.dll + 0xf51d2	0x7ff9ec9451d2	C:\WINDOWS\assembly\NativeImages_v4.0.30319_64\Microsoft.D487c049b#\17aa6534ea5939f3df10e1f242a027a9\Microsoft.Developer.IdentityService.Client.ni.dll
  37	Microsoft.Developer.IdentityService.Client.ni.dll	Microsoft.Developer.IdentityService.Client.ni.dll + 0x109ca0	0x7ff9ec959ca0	C:\WINDOWS\assembly\NativeImages_v4.0.30319_64\Microsoft.D487c049b#\17aa6534ea5939f3df10e1f242a027a9\Microsoft.Developer.IdentityService.Client.ni.dll
  38	Microsoft.VisualStudio.Shell.Connected.ni.dll	Microsoft.VisualStudio.Shell.Connected.ni.dll + 0x6144f8	0x7ffa32cd44f8	C:\WINDOWS\assembly\NativeImages_v4.0.30319_64\Microsoft.V54ab70ba#\d22e978717b6a100f57a0e732b0287ad\Microsoft.VisualStudio.Shell.Connected.ni.dll
  ```

  - By placing "rundll32.exe" in the project root location, the attacker code can be executed.
  ```
  "C:\Windows\System32\rundll32.exe" url.dll, FileProtocolHandler https://github.com/login/oauth/authorize?client_id=a200baed193bb2088a6e&redirect_uri=http%3A%2F%2Flocalhost%3A57142%2F&scope=user%2Crepo%2Cgist%2Cwrite%3Apublic_key%2Cread%3Aorg%2Cworkflow&state=c9ca368c-aa67-4a62-9f78-777e4d2244dc
  ```
  






## Case 1. Git clone repo and execute

- Refer to the poc video

