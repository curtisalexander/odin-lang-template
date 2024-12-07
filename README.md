# odin-lang-template
[Odin language](https://odin-lang.org/) template

## Features
- Utilize [Odin language server](https://github.com/DanielGavin/ols)
- Configure Sublime [build system](https://www.sublimetext.com/docs/build_systems.html)
- Ensure no memory leaks through use of [tracking allocator](https://pkg.odin-lang.org/core/mem/#tracking_allocator)

## Editor Configuration
Editor configuration for [Sublime Text](https://www.sublimetext.com/)

### `Build`
Contents of `%APPDATA%\Sublime Text\Packages\User\Odin.sublime-build`

```js
{
	"selector": "source.odin",
	"file_regex": "^(.+)\\(([0-9]+):([0-9]+)\\) (.+)$",
	"file_patterns": ["*.odin"],
	"shell_cmd": ["odin check ."],
	"variants": [
		// build 
		{"name":"build", "shell_cmd":"odin build ."},
		// check
		{"name":"check", "shell_cmd":"odin check ."},
		// run
		{"name":"run", "shell_cmd":"odin run ."},
		// test
		{"name":"test", "shell_cmd":"odin test ."},
	]
}
```

### `LSP`
Contents of `%APPDATA%\Sublime Text\Packages\User\LSP.sublime-settings`

```js
// Settings in here override those in "LSP/LSP.sublime-settings"
{
	"clients": {
		"odin": {
			"command": [
				"C:\\path\\ols\\ols.exe"
			],
			"enabled": false, // true for globally-enabled, but not required due to 'Enable In Project' command
			"selector": "source.odin",
			"initializationOptions": {
				"enable_semantic_tokens": true,
				"enable_document_symbols": true,
				"enable_hover": true,
				"enable_snippets": true,
				"enable_format": true,
			}
		}
	}
}
```

Set `ODIN_ROOT` environment variable to path of Odin directory (which contains `core` and `vendor` libraries).

```cmd
# from Windows cmd prompt
rundll32 sysdm.cpl,EditEnvironmentVariables
```

## Sources
- [DanielGavin - ols](https://github.com/DanielGavin/ols)
- [enerqi - odin-lang-skeleton](https://github.com/enerqi/odin-lang-skeleton)
- [Karl Zylinski](https://zylinski.se/)
	- [Sublime Text + Odin + Code completion](https://youtu.be/RF2MgVqfBV8?si=aStvXDnIw8xjGB_0)
	- [Tracking memory leaks](https://zylinski.se/posts/introduction-to-odin/#tracking-memory-leaks)
	- [Tracking allocator example](https://gist.github.com/karl-zylinski/4ccf438337123e7c8994df3b03604e33)
	- [Using Odinlang's Tracking Allocator](https://youtu.be/dg6qogN8kIE?si=dM4JkxsYL8vcGVWC)
- [Sublime Text](https://www.sublimetext.com/)
	- [Build Systems](https://www.sublimetext.com/docs/build_systems.html)
	- [LSP - Client Configuration](https://lsp.sublimetext.io/client_configuration/)
	- [Projects](https://www.sublimetext.com/docs/projects.html)
