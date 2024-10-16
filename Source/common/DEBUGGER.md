# PDB based debugger

This debugger uses [`pdb`](https://docs.python.org/3/library/pdb.html) to start a
python file. It then translates all
[`DAP`](https://microsoft.github.io/debug-adapter-protocol/overview) messages into
pdb commands in order to allow debugging in VS code.

For example, this message:

```json
{
	"command": "setBreakpoints",
	"arguments": {
		"source": {
			"name": "test_longoutput.py",
			"path": "d:\\Source\\Testing\\Testing_Pyright\\test_longoutput.py"
		},
		"lines": [3],
		"breakpoints": [
			{
				"line": 3
			}
		],
		"sourceModified": false
	},
	"type": "request",
	"seq": 3
}
```

Gets translated into the pdb `b(reak)` command:

```
b d:\\Source\\Testing\\Testing_Pyright\\test_longoutput.py:3
```

# Left to do

-   Test to write
    -   Multiple files involved
    -   recursion and stack changing
    -   taking input from user
    -   what happens with threads
-   Exception handling (stop on caught)
