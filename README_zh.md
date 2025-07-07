# MCP 使用时配置工具 (MCP Config During Use)

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.12+-blue.svg)](https://python.org)
[![Dify 插件](https://img.shields.io/badge/Dify-插件-green.svg)](https://dify.ai)
[![许可证](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![版本](https://img.shields.io/badge/Version-1.0.0-red.svg)](https://github.com/your-repo/releases)

这是一个Dify插件，支持在运行时动态配置MCP协议服务器，具备先进的传输策略支持。

[English](README.md) | [中文简体](#中文简体)

</div>

---

## 🚀 核心特性

### 🔄 **多传输策略支持**
- **SSE (服务器推送事件)**: 实时双向通信
- **Streamable HTTP**: 基于HTTP的流式传输，支持会话管理
- **智能检测**: 自动检测服务器支持的传输协议

### 🔧 **高级功能**
- ✅ **运行时配置**: 每次调用时单独配置MCP服务器
- ✅ **传输自动检测**: 基于服务器能力的智能协议检测
- ✅ **HTTP重定向支持**: 无缝重定向处理
- ✅ **会话管理**: Streamable HTTP的持久会话
- ✅ **灵活头部**: 支持自定义HTTP头部进行认证
- ✅ **超时控制**: 可配置的超时参数

### 🛠 **工具列表**
| 工具名称 | 功能描述 | 使用场景 |
|---------|----------|----------|
| **mcp_list_tools** | 列出可用工具 | 发现MCP服务器功能 |
| **mcp_call_tool** | 执行特定工具 | 调用MCP服务器功能 |

---

## 📖 使用指南

### 🔍 **列出MCP工具**

发现MCP服务器上所有可用的工具：

**参数说明:**
- `server_url` **(必填)**: MCP服务器端点URL
- `headers` *(可选)*: HTTP请求头，JSON格式
- `timeout` *(可选)*: HTTP请求超时时间（秒）
- `sse_read_timeout` *(可选)*: SSE读取超时时间（秒）

**示例:**
```json
{
  "server_url": "http://127.0.0.1:8000/sse",
  "headers": "{\"Authorization\":\"Bearer your_token\"}",
  "timeout": 60,
  "sse_read_timeout": 300
}
```

### ⚡ **调用MCP工具**

在MCP服务器上执行特定工具：

**参数说明:**
- `server_url` **(必填)**: MCP服务器端点URL
- `headers` *(可选)*: HTTP请求头，JSON格式
- `timeout` *(可选)*: HTTP请求超时时间（秒）
- `sse_read_timeout` *(可选)*: SSE读取超时时间（秒）
- `tool_name` **(必填)**: 要调用的工具名称
- `arguments` **(必填)**: 工具参数，JSON格式

**示例:**
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

## ⚠️ **重要说明**

### **传输配置**
- 插件自动检测服务器支持的传输协议
- SSE优先用于实时通信
- Streamable HTTP作为回退或特殊需求使用

### **JSON参数处理**
- `headers`和`arguments`中的所有JSON对象必须进行字符串编码
- 确保JSON字符串中的双引号正确转义

### **超时配置考虑**
- 调整`timeout`用于连接建立
- 配置`sse_read_timeout`用于长时间运行的操作
- 在超时设置中考虑网络延迟

### **会话管理**
- Streamable HTTP自动管理会话ID
- 会话在多个请求间保持
- 会话清理自动处理

---

## 🔄 **传输策略详解**

### **SSE传输策略**
- **特点**: 实时双向通信，事件驱动
- **适用场景**: 需要实时响应的应用
- **优势**: 低延迟，自动重连，事件流式处理

### **Streamable HTTP传输策略**
- **特点**: 基于HTTP的流式传输，支持会话
- **适用场景**: 需要会话保持的应用
- **优势**: 会话管理，跨请求状态保持，集群模式支持

### **自动检测机制**
1. **协议探测**: 首先尝试Streamable HTTP
2. **回退策略**: 失败时自动切换到SSE
3. **智能选择**: 根据服务器能力选择最优策略

---

## 📄 **许可证**

本项目基于MIT许可证开源 - 查看 [LICENSE](LICENSE) 文件了解详情。

---

<div align="center">

**用 ❤️ 为Dify社区制作**

⭐ **如果觉得有用，请给我们一个星标！** ⭐

</div> 