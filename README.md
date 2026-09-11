# mcp-snippetbox

A small MCP server exposing my notes to Claude Desktop

## Install

```bash
pip install -r requirements.txt
```

## How to use

```bash
# claude_desktop_config.json  (use ABSOLUTE paths: Claude does not
# run from the repo directory, so a bare "server.py" is not found)
# {
#   "mcpServers": {
#     "notes-box": {
#       "command": "python",
#       "args": ["/abs/path/to/mcp-snippetbox/server.py"],
#       "env": {"MCP_NOTES_FILE": "/abs/path/to/notes.json"}
#     }
#   }
# }
python server.py --help
```

## Highlights

- Notes path set by MCP_NOTES_FILE or --notes-file
- Includes a Claude Desktop config snippet with absolute paths
- A missing note raises instead of returning the string 'not found'
- Every tool carries a real docstring, so clients get descriptions
- Five tools: add / get / update / delete / list notes
- Atomic saves (temp file + os.replace) behind a write lock

## Project structure

```text
├── .github/
│   └── workflows/
│       └── ci.yml
├── docs/
│   ├── development.md
│   ├── faq.md
│   └── usage.md
├── tests/
│   └── test_notes.py
├── .editorconfig
├── .gitignore
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE
├── SECURITY.md
├── requirements.txt
└── server.py
```

## Development

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python -m pytest -q
```

## License

MIT. Do whatever you want.
