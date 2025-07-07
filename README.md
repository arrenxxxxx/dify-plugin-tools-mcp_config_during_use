# MCP Config During Use

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.12+-blue.svg)](https://python.org)
[![Dify Plugin](https://img.shields.io/badge/Dify-Plugin-green.svg)](https://dify.ai)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0.0-red.svg)](https://github.com/your-repo/releases)

A Dify plugin that enables dynamic MCP (Model Context Protocol) server configuration during runtime with advanced transport strategy support.

[English](#english) | [中文简体](README_zh.md)

</div>

---

## 🚀 Features

### 🔄 **Multiple Transport Strategies**
- **SSE (Server-Sent Events)**: Real-time bidirectional communication
- **Streamable HTTP**: HTTP-based streaming with session management
- **Auto Detection**: Automatically detects server-supported transport protocols

### 🔧 **Advanced Capabilities**
- ✅ **Runtime Configuration**: Configure MCP servers during each call
- ✅ **Transport Auto-Detection**: Smart protocol detection based on server capabilities
- ✅ **HTTP Redirect Support**: Seamless redirect handling
- ✅ **Session Management**: Persistent sessions for Streamable HTTP
- ✅ **Flexible Headers**: Custom HTTP headers for authentication
- ✅ **Timeout Control**: Configurable timeout parameters

### 🛠 **Tool Arsenal**
| Tool | Description | Purpose |
|------|-------------|---------|
| **mcp_list_tools** | List available tools | Discover MCP server capabilities |
| **mcp_call_tool** | Execute specific tools | Invoke MCP server functions |

---

## 📖 Usage Guide

### 🔍 **List MCP Tools**

Discover all available tools on an MCP server:

**Parameters:**
- `server_url` **(required)**: MCP server endpoint URL
- `headers` *(optional)*: HTTP headers in JSON format
- `timeout` *(optional)*: HTTP request timeout (seconds)
- `sse_read_timeout` *(optional)*: SSE read timeout (seconds)

**Example:**
```json
{
  "server_url": "http://127.0.0.1:8000/sse",
  "headers": "{\"Authorization\":\"Bearer your_token\"}",
  "timeout": 60,
  "sse_read_timeout": 300
}
```

### ⚡ **Call MCP Tool**

Execute a specific tool on an MCP server:

**Parameters:**
- `server_url` **(required)**: MCP server endpoint URL
- `headers` *(optional)*: HTTP headers in JSON format
- `timeout` *(optional)*: HTTP request timeout (seconds)
- `sse_read_timeout` *(optional)*: SSE read timeout (seconds)
- `tool_name` **(required)**: Name of the tool to execute
- `arguments` **(required)**: Tool arguments in JSON format

**Example:**
```json
{
  "server_url": "http://127.0.0.1:8000/sse",
  "headers": "{\"Authorization\":\"Bearer your_token\"}",
  "timeout": 60,
  "sse_read_timeout": 300,
  "tool_name": "example_tool",
  "arguments": "{\"param1\":\"value1\",\"param2\":123}"
}
```

---

## ⚠️ **Important Notes**

### **Transport Configuration**
- The plugin automatically detects server-supported transport protocols
- SSE is preferred for real-time communication
- Streamable HTTP is used as fallback or for specific requirements

### **JSON Parameter Handling**
- All JSON objects in `headers` and `arguments` must be string-encoded
- Ensure proper double-quote escaping in JSON strings

### **Timeout Considerations**
- Adjust `timeout` for connection establishment
- Configure `sse_read_timeout` for long-running operations
- Consider network latency in timeout settings

### **Session Management**
- Streamable HTTP automatically manages session IDs
- Sessions are maintained across multiple requests
- Session cleanup is handled automatically

---

## 📄 **License**

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Made with ❤️ for the Dify Community**

⭐ **Star this repo if you find it useful!** ⭐

</div> 