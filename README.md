# Source Code X

🟆 [mSCX.py](http://www.micah-t.xyz)

![Release](https://img.shields.io/github/v/release/micah0912/mSCL.py?style=flat-square&color=blue)
![Stability-Beta](https://img.shields.io/badge/stability-mature-blue.svg?style=flat-square)
[![Licence-GPLv3](https://img.shields.io/badge/license-GPLv3-blue.svg?style=flat-square)](https://github.com/micah0912/SCL.py/blob/master/LICENSE)
![Requirement-Paython-3.10](https://img.shields.io/badge/paython-%3E=3.10-blue.svg?style=flat-square)

- The underline logic of monster utility.
- Provide ability to 
	- glob and filter target files;
	- store settings based on each hierarchy.
- Based on [spairaru.py](https://github.com/etrotech/spairaru.py) framework.

<tab>
<br> 

### Spinoff
---

🟆 [mSCL.py](https://github.com/micah0912/mSCL.py)
 - Source Code License Manager

🟆 [mSCF.py](https://github.com/micah0912/mSCF.py)
 - Source Code Format Manager
 
🟆 [mSCO.py](https://github.com/micah0912/mSCO.py)
 - Source Code Obfuscation Manager

<tab>
<br> 

### Advanced Usage
---

`aply_gitign` :
- Remove any folders and files listing in .gitignore. Preferred option when a distribution folder is given.
- Defaults to `false`.

`distribution_directory` :
- When distribution directory is giving, original directory will be copied over and start process from there. 
- Defautls to `""`.

`follow_link` :
- If processing file is a symbolic link, edit the source file instead.
- Defaults to `false`.

`ignore_symbolic_link` :
- When the `distribution_directory` option is given, copying will skip folders and files if they are symbolic links.
- Defaults to `false`.

`keep_symbolic_link` :
- When the `distribution_directory` option is given, create new symbolic link from source if they are symbolic links.
- Defaults to `true`.

`overwrite` :
- When the `distribution_directory` option is given, copying will overwrite existing folders and files.
- Otherwise will stop.
- Defaults to `false`.

`recursive` :
- Processing will not stop at first directory, will continue to all files in all subfolders. 
- Defaults to `false`.

`verbose` :
- Display log or not.
- Defaults to `true`.

<tab>
<br> 

### Customization
---
- Customize settings by storing custom files within the designated **.scx** folder or application-specific folders.
- **SCX** will systematically retrieve custom files from **.scx** folder and application-specific folders in every directory.
- Settings will be structured hierarchically, inheriting from their parent directories.

*Example Hierarchy*

```

🏠
├─ 🖿 .scx 👈 // root configurations
│  └─ ...
├─ 🖿 A
│  ├─ 🖿 .scx 👈 // A configurations
│  │  └─ ...
│  ├─ 🖿 B
│  │  ├─ 🖿 .scx 👈 // B configurations
│  │  │  └─ ...
│  │  └─ ...
│  └─ ...
├─ 🖿 C
│  ├─ 🖿 .scx 👈 // C configurations
│  │  └─ ...
│  ├─ 🖿 D
│  │  ├─ 🖿 .scx 👈 // D configurations
│  │  │  └─ ...
│  │  └─ ...
│  └─ ...
└─ ...

B will inherit configurations from root and A. 
D will inherit configurations from root and C. 

```

<tab>
<br> 

### Custom - Configuration
---

- **.cnf**, the Configuration file stores predefined variables. It accepts syntax from standard **.conf**, **.env** or **.ini** files.
- Alternatively, you may use the **.env** or **.ini** file extensions.
- The file may or may not include section names.

*Example Hierarchy*

```

🏠
├─ 🖿 .scx
│  ├─ 🖺 xxx.apv
│  ├─ 🖺 xxx.env 👈
│  ├─ 🖺 xxx.cnf 👈
│  ├─ 🖺 xxx.ign
│  ├─ 🖺 xxx.ini 👈
│  └─ ...
└─ ...

```

*Exanple of xxx.ini*

```

[__section_name_]
__custom_var_Name__=__Custom_Var_Value__
...

```

<tab>  
<br>

### Custom - Approve and Ignore
---

- **.apv**, the Approve fil is utilized to filter out files during globing processes.
- **.ign**, the Ignore file provides additional filtration beyond **.apv** results.
- The syntax of rules resembles that of <u>.gitignore</u>.
- Filters are applied in the following order:
	1. **.apv** 
	2. **.ign**

<br>

*Example Hierarchy*

```

🏠
├─ 🖿 .scx
│  ├─ 🖺 xxx.apv 👈
│  ├─ 🖺 xxx.env
│  ├─ 🖺 xxx.cnf
│  ├─ 🖺 xxx.ign 👈
│  ├─ 🖺 xxx.ini
│  └─ ...
└─ ...

```

*Exanple of xxx.ign*

```

**/__folder_name__
*.__extension__

```

<tab>  
<br>

### Custom - Filter
---

**SCX** enables you to modify results by adding filter listener throughs [spairaru.py](https://github.com/etrotech/spairaru.py) framework.

<br>

**SourceCodeDocumentFilter** : 
- Contains Filters used to manage document.

<br>

*Example of Filter assignment*
<details>
<summary>long syntax</summary>
<br>

```python

from {{ __pkacge_name__ }} import {{ __application_name__ }} as scx
from {{ __pkacge_name__ }} import SourceCodeDocumentFilter

scx.filter(
	# filter_name
	SourceCodeDocumentFilter.FinalContent
	# filter_listener
	, (
		lambda
			Filter__
			, original_cntent__
			, TargetFile__
		:
			return "{{ __modified_content__ }}"
	)
)

```

</details>

<details>
<summary>short syntax</summary>
<br>

```python

from {{ __pkacge_name__ }} import {{ __application_name__ }} as scx
from {{ __pkacge_name__ }} import ScDocFltr

scx.fltr(
	# filter_name
	ScDocFltr.FinCnt
	# filter_listener
	, (
		lambda
			Fltr__
			, orig_cnt__
			, TgtFl__
		:
			return "{{ __modified_content__ }}"
	)
)

```

</details>

<tab>  
<br>

### ☕
---

If you feel this app useful and helpful, please support me to make it better.

<p style="float: left;">
	<a href="https://paypal.me/micaht0912" target="_blank"><img src="https://raw.githubusercontent.com/micah0912/M/master/__readme__/ast/m-paypal.jpg" alt="Paypal" style="width: 24%; "></a>
	<a href="" target="_blank"><img src="https://raw.githubusercontent.com/micah0912/M/master/__readme__/ast/m-alipay.jpg" alt="Alipay" style=" width: 24%;"></a>
	<a href="" target="_blank"><img src="https://raw.githubusercontent.com/micah0912/M/master/__readme__/ast/m-wechat.jpg" alt="Wechat" style="width: 24%;"></a>
</p>

<br>
