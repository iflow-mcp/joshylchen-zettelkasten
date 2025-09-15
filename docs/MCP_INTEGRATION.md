
# MCP Integration Guide

This project exposes **tools** suitable for registration with the Model Context Protocol (MCP).
A minimal scaffold is provided in `zettelkasten_assistant/server/mcp_server.py`.

## Options

1. **Use FastAPI endpoints** from an MCP gateway that maps HTTP APIs to MCP tools.
2. **Use a native MCP Python library** (e.g., `fastmcp` or `modelcontextprotocol`) and register tools directly:

Example (pseudo-code):
```python
from fastmcp import MCP

mcp = MCP(name="zk-assistant", version="0.1.0")
@mcp.tool(name="zk_create_note", description="Create a ZK note")
def zk_create_note(title: str, body: str, tags: list[str] = []):
    ... # call CEQRC.create_seed(...)
mcp.run()
```

## Recommended Tools
- `zk_create_note(title, body, tags)`
- `zk_search(q, tag=None)`
- `zk_update_note(id, title, body, tags)`
- `zk_get_note(id)`
- `zk_create_link(source_id, target_id, type)`
- `zk_run_ceqrc(id)`

Please refer to the MCP server registry contribution guide for metadata, security, and deployment requirements.
