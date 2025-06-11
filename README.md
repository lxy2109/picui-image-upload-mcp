# Picui 图床 MCP Server

本项目是基于 [PICUI 图床](https://picui.cn/) 的多功能 API 封装，支持用户资料、策略列表、Token 生成、图片上传、图片列表、删除图片、相册列表、删除相册等操作，适用于 MCP 智能体工具集成。

## 依赖环境
- Python 3.8+
- 依赖包见 `requirements.txt`

## 快速开始
1. 安装依赖：
   ```bash
   pip install -r requirements.txt
   ```
2. 配置 `mcpjson`（见下方示例）
3. 运行服务：
   ```bash
   python server.py
   ```

## mcpjson 配置示例
见 `mcpjson.example` 文件：
```json
{
    "mcpServers":{
        "Picui": {
            "command": "python",
            "args": [
                "your_abs_dir/picui-image-upload-mcp/server.py"
            ],
            "env": {
                "PICUI_TOKEN": "your_token"
            }
        }
    }
}
```
- `PICUI_TOKEN`：你的 Bearer Token，可在 Picui 个人中心获取。

## 工具功能
- 用户资料查询
- 策略列表
- Token 生成
- 图片上传
- 图片列表
- 删除图片
- 相册列表
- 删除相册

## 使用示例
以图片上传为例：
```python
from server import picui_api, PicuiApiParams
import asyncio

params = PicuiApiParams(action='upload_image', file_path='test.jpg')
result = asyncio.run(picui_api(params))
print(result)
```

## 许可证
MIT 