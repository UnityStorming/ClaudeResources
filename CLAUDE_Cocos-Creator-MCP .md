##  把下面内容复制到你自己工程根目录的 CLAUDE.md 中，如果没有该文件，在Claude code中执行 /init 他会自己生成



## Cocos Creator MCP 工具索引

通过 `cocos-creator` MCP（`http://127.0.0.1:3000/mcp`）可直接操控 Cocos Creator 编辑器。以下按功能分类列出全部可用工具。

### 1. Scene — 场景管理

| 工具 | 说明 | 关键参数 |
|------|------|----------|
| `scene_get_current_scene` | 获取当前场景信息 | — |
| `scene_get_scene_list` | 获取项目所有场景列表 | — |
| `scene_open_scene` | 打开场景 | `scenePath` |
| `scene_save_scene` | 保存当前场景 | — |
| `scene_create_scene` | 创建新场景 | `sceneName`, `savePath`（如 `db://assets/scenes/Game.scene`） |
| `scene_save_scene_as` | 另存为 | `path` |
| `scene_close_scene` | 关闭当前场景 | — |
| `scene_get_scene_hierarchy` | 获取场景层级树 | `includeComponents`（bool） |

### 2. Node — 节点操作

| 工具 | 说明 | 关键参数 |
|------|------|----------|
| `node_create_node` | 创建节点（空节点/带组件/实例化预制体） | `name`, `parentUuid`, `nodeType`(Node/2DNode/3DNode), `components[]`, `assetPath`, `initialTransform` |
| `node_get_node_info` | 获取节点信息 | `uuid` |
| `node_find_nodes` | 按名称模式搜索节点 | `pattern`, `exactMatch` |
| `node_find_node_by_name` | 精确名称查找节点 | `name` |
| `node_get_all_nodes` | 获取场景中全部节点及 UUID | — |
| `node_set_node_property` | 设置节点属性（active/name/layer） | `uuid`, `property`, `value` |
| `node_set_node_transform` | 设置位置/旋转/缩放（自动区分 2D/3D） | `uuid`, `position{x,y,z}`, `rotation{x,y,z}`, `scale{x,y,z}` |
| `node_delete_node` | 删除节点 | `uuid` |
| `node_move_node` | 移动节点到新父节点 | `nodeUuid`, `newParentUuid`, `siblingIndex` |
| `node_duplicate_node` | 复制节点 | `uuid`, `includeChildren` |
| `node_detect_node_type` | 检测节点是 2D 还是 3D | `uuid` |

### 3. Component — 组件操作

| 工具 | 说明 | 关键参数 |
|------|------|----------|
| `component_add_component` | 添加组件 | `nodeUuid`, `componentType`（如 `cc.Sprite`, `cc.Label`） |
| `component_remove_component` | 移除组件（需用 cid） | `nodeUuid`, `componentType`（cid） |
| `component_get_components` | 获取节点所有组件 | `nodeUuid` |
| `component_get_component_info` | 获取组件详情 | `nodeUuid`, `componentType` |
| `component_set_component_property` | 设置组件属性 | `nodeUuid`, `componentType`, `property`, `propertyType`(string/number/color/vec2/vec3/size/node/spriteFrame...), `value` |
| `component_attach_script` | 挂载脚本组件 | `nodeUuid`, `scriptPath`（如 `db://assets/scripts/core/GameMain.ts`） |
| `component_get_available_components` | 获取可用组件类型列表 | `category`(all/renderer/ui/physics/animation/audio) |

### 4. Prefab — 预制体管理

| 工具 | 说明 | 关键参数 |
|------|------|----------|
| `prefab_get_prefab_list` | 获取项目所有预制体 | `folder` |
| `prefab_load_prefab` | 加载预制体 | `prefabPath` |
| `prefab_instantiate_prefab` | 实例化预制体到场景 | `prefabPath`, `parentUuid`, `position{x,y,z}` |
| `prefab_create_prefab` | 从节点创建预制体 | `nodeUuid`, `savePath`, `prefabName` |
| `prefab_update_prefab` | 更新预制体 | `prefabPath`, `nodeUuid` |
| `prefab_revert_prefab` | 还原预制体实例 | `nodeUuid` |
| `prefab_get_prefab_info` | 获取预制体详情 | `prefabPath` |
| `prefab_validate_prefab` | 验证预制体格式 | `prefabPath` |
| `prefab_duplicate_prefab` | 复制预制体 | `sourcePrefabPath`, `targetPrefabPath`, `newPrefabName` |
| `prefab_restore_prefab_node` | 从资产恢复预制体节点 | `nodeUuid`, `assetUuid` |

### 5. Project — 项目与资产管理

| 工具 | 说明 | 关键参数 |
|------|------|----------|
| `project_get_project_info` | 获取项目信息 | — |
| `project_get_project_settings` | 获取项目设置 | `category`(general/physics/render/assets) |
| `project_run_project` | 预览运行 | `platform`(browser/simulator/preview) |
| `project_build_project` | 构建项目 | `platform`(web-mobile/web-desktop/ios/android/windows/mac), `debug` |
| `project_get_build_settings` | 获取构建设置 | — |
| `project_open_build_panel` | 打开构建面板 | — |
| `project_check_builder_status` | 检查构建器是否就绪 | — |
| `project_start_preview_server` | 启动预览服务器 | `port`(默认 7456) |
| `project_stop_preview_server` | 停止预览服务器 | — |
| `project_refresh_assets` | 刷新资产数据库 | `folder` |
| `project_import_asset` | 导入资产文件 | `sourcePath`, `targetFolder` |
| `project_get_asset_info` | 获取资产信息 | `assetPath`（如 `db://assets/...`） |
| `project_get_asset_details` | 获取资产详情（含子资产） | `assetPath`, `includeSubAssets` |
| `project_get_assets` | 按类型获取资产列表 | `type`(all/scene/prefab/script/texture/material/mesh/audio/animation), `folder` |
| `project_find_asset_by_name` | 按名称搜索资产 | `name`, `assetType`, `exactMatch`, `folder`, `maxResults` |
| `project_create_asset` | 创建资产文件或文件夹 | `url`, `content`, `overwrite` |
| `project_copy_asset` | 复制资产 | `source`, `target`, `overwrite` |
| `project_move_asset` | 移动资产 | `source`, `target`, `overwrite` |
| `project_delete_asset` | 删除资产 | `url` |
| `project_save_asset` | 保存资产内容 | `url`, `content` |
| `project_reimport_asset` | 重新导入资产 | `url` |
| `project_query_asset_path` | 获取资产磁盘路径 | `url` |
| `project_query_asset_uuid` | URL → UUID | `url` |
| `project_query_asset_url` | UUID → URL | `uuid` |

### 6. Debug — 调试与日志

| 工具 | 说明 | 关键参数 |
|------|------|----------|
| `debug_get_console_logs` | 获取编辑器控制台日志 | `filter`(all/log/warn/error/info), `limit` |
| `debug_clear_console` | 清空控制台 | — |
| `debug_execute_script` | 在场景上下文执行 JS 脚本 | `script` |
| `debug_get_node_tree` | 获取调试节点树 | `rootUuid`, `maxDepth` |
| `debug_get_performance_stats` | 获取性能统计 | — |
| `debug_validate_scene` | 验证场景问题 | `checkMissingAssets`, `checkPerformance` |
| `debug_get_editor_info` | 获取编辑器/环境信息 | — |
| `debug_get_project_logs` | 获取项目日志文件 | `lines`, `logLevel`(ERROR/WARN/INFO/DEBUG/TRACE/ALL), `filterKeyword` |
| `debug_get_log_file_info` | 获取日志文件信息 | — |
| `debug_search_project_logs` | 搜索项目日志（支持正则） | `pattern`, `maxResults`, `contextLines` |

### 7. SceneAdvanced — 场景高级操作

| 工具 | 说明 | 关键参数 |
|------|------|----------|
| `sceneAdvanced_reset_node_property` | 重置节点属性为默认值 | `uuid`, `path` |
| `sceneAdvanced_reset_node_transform` | 重置位置/旋转/缩放 | `uuid` |
| `sceneAdvanced_reset_component` | 重置组件为默认值 | `uuid`（组件 UUID） |
| `sceneAdvanced_copy_node` | 复制节点 | `uuids`（string 或 string[]） |
| `sceneAdvanced_paste_node` | 粘贴节点 | `target`, `uuids`, `keepWorldTransform` |
| `sceneAdvanced_cut_node` | 剪切节点 | `uuids` |
| `sceneAdvanced_move_array_element` | 移动数组元素位置 | `uuid`, `path`, `target`, `offset` |
| `sceneAdvanced_remove_array_element` | 移除数组元素 | `uuid`, `path`, `index` |
| `sceneAdvanced_restore_prefab` | 从资产恢复预制体实例 | `nodeUuid`, `assetUuid` |
| `sceneAdvanced_execute_component_method` | 执行组件方法 | `uuid`（组件）, `name`, `args[]` |
| `sceneAdvanced_execute_scene_script` | 执行场景脚本方法 | `name`（插件名）, `method`, `args[]` |
| `sceneAdvanced_scene_snapshot` | 创建场景快照 | — |
| `sceneAdvanced_scene_snapshot_abort` | 取消场景快照 | — |
| `sceneAdvanced_begin_undo_recording` | 开始 Undo 录制 | `nodeUuid` → 返回 `undoId` |
| `sceneAdvanced_end_undo_recording` | 结束 Undo 录制 | `undoId` |
| `sceneAdvanced_cancel_undo_recording` | 取消 Undo 录制 | `undoId` |
| `sceneAdvanced_soft_reload_scene` | 软重载当前场景 | — |
| `sceneAdvanced_query_scene_ready` | 检查场景是否就绪 | — |
| `sceneAdvanced_query_scene_dirty` | 检查场景是否有未保存更改 | — |
| `sceneAdvanced_query_scene_classes` | 查询已注册的类 | `extends`（基类过滤） |
| `sceneAdvanced_query_scene_components` | 查询可用场景组件 | — |
| `sceneAdvanced_query_component_has_script` | 检查组件是否有脚本 | `className` |
| `sceneAdvanced_query_nodes_by_asset_uuid` | 查找使用指定资产的节点 | `assetUuid` |

### 8. SceneView — 场景视图控制

| 工具 | 说明 | 关键参数 |
|------|------|----------|
| `sceneView_change_gizmo_tool` | 切换 Gizmo 工具 | `name`(position/rotation/scale/rect) |
| `sceneView_query_gizmo_tool_name` | 查询当前 Gizmo 工具 | — |
| `sceneView_change_gizmo_pivot` | 切换变换基准点 | `name`(pivot/center) |
| `sceneView_query_gizmo_pivot` | 查询当前基准点 | — |
| `sceneView_query_gizmo_view_mode` | 查询视图模式 | — |
| `sceneView_change_gizmo_coordinate` | 切换坐标系 | `type`(local/global) |
| `sceneView_query_gizmo_coordinate` | 查询当前坐标系 | — |
| `sceneView_change_view_mode_2d_3d` | 切换 2D/3D 视图 | `is2D`(bool) |
| `sceneView_query_view_mode_2d_3d` | 查询当前视图模式 | — |
| `sceneView_set_grid_visible` | 显示/隐藏网格 | `visible`(bool) |
| `sceneView_query_grid_visible` | 查询网格可见性 | — |
| `sceneView_set_icon_gizmo_3d` | 设置图标 Gizmo 2D/3D 模式 | `is3D`(bool) |
| `sceneView_query_icon_gizmo_3d` | 查询图标 Gizmo 模式 | — |
| `sceneView_set_icon_gizmo_size` | 设置图标 Gizmo 大小 | `size`(10-100) |
| `sceneView_query_icon_gizmo_size` | 查询图标 Gizmo 大小 | — |
| `sceneView_focus_camera_on_nodes` | 聚焦相机到节点 | `uuids[]`（null 聚焦全部） |
| `sceneView_align_camera_with_view` | 将场景相机应用到选中节点 | — |
| `sceneView_align_view_with_node` | 将选中节点视角应用到视图 | — |
| `sceneView_get_scene_view_status` | 获取场景视图综合状态 | — |
| `sceneView_reset_scene_view` | 重置场景视图为默认 | — |

### 9. Preferences — 编辑器偏好设置

| 工具 | 说明 | 关键参数 |
|------|------|----------|
| `preferences_open_preferences_settings` | 打开偏好设置面板 | `tab`(general/external-tools/data-editor/laboratory/extensions) |
| `preferences_query_preferences_config` | 查询偏好配置 | `name`, `path`, `type`(default/global/local) |
| `preferences_set_preferences_config` | 设置偏好配置 | `name`, `path`, `value`, `type` |
| `preferences_get_all_preferences` | 获取所有偏好分类 | — |
| `preferences_reset_preferences` | 重置偏好为默认值 | `name`, `type`(global/local) |
| `preferences_export_preferences` | 导出偏好配置 | `exportPath` |
| `preferences_import_preferences` | 导入偏好配置 | `importPath` |

### 10. Server — 编辑器服务器信息

| 工具 | 说明 |
|------|------|
| `server_query_server_ip_list` | 查询服务器 IP 列表 |
| `server_query_sorted_server_ip_list` | 获取排序后的 IP 列表 |
| `server_query_server_port` | 查询编辑器服务端口 |
| `server_get_server_status` | 获取综合服务器状态 |
| `server_check_server_connectivity` | 检查服务器连通性（`timeout` ms） |
| `server_get_network_interfaces` | 获取可用网络接口 |

### 11. Broadcast — 广播消息

| 工具 | 说明 | 关键参数 |
|------|------|----------|
| `broadcast_get_broadcast_log` | 获取广播消息日志 | `messageType`, `limit` |
| `broadcast_listen_broadcast` | 监听广播消息 | `messageType` |
| `broadcast_stop_listening` | 停止监听 | `messageType` |
| `broadcast_clear_broadcast_log` | 清空广播日志 | — |
| `broadcast_get_active_listeners` | 获取活跃监听器列表 | — |

### 12. ReferenceImage — 参考图

| 工具 | 说明 | 关键参数 |
|------|------|----------|
| `referenceImage_add_reference_image` | 添加参考图 | `paths[]`（绝对路径） |
| `referenceImage_remove_reference_image` | 移除参考图 | `paths[]` |
| `referenceImage_switch_reference_image` | 切换参考图 | `path`, `sceneUUID` |
| `referenceImage_set_reference_image_data` | 设置参考图属性 | `key`(path/x/y/sx/sy/opacity), `value` |
| `referenceImage_query_reference_image_config` | 查询参考图配置 | — |
| `referenceImage_query_current_reference_image` | 查询当前参考图 | — |
| `referenceImage_refresh_reference_image` | 刷新参考图显示 | — |
| `referenceImage_set_reference_image_position` | 设置位置 | `x`, `y` |
| `referenceImage_set_reference_image_scale` | 设置缩放 | `sx`, `sy`(0.1-10) |
| `referenceImage_set_reference_image_opacity` | 设置透明度 | `opacity`(0-1) |
| `referenceImage_list_reference_images` | 列出所有参考图 | — |
| `referenceImage_clear_all_reference_images` | 清空所有参考图 | — |

### 13. AssetAdvanced — 资产高级操作

| 工具 | 说明 | 关键参数 |
|------|------|----------|
| `assetAdvanced_save_asset_meta` | 保存资产 Meta 信息 | `urlOrUUID`, `content` |
| `assetAdvanced_generate_available_url` | 生成可用的资产 URL | `url` |
| `assetAdvanced_query_asset_db_ready` | 检查资产数据库是否就绪 | — |
| `assetAdvanced_open_asset_external` | 用外部程序打开资产 | `urlOrUUID` |
| `assetAdvanced_batch_import_assets` | 批量导入资产 | `sourceDirectory`, `targetDirectory`, `fileFilter[]`, `recursive`, `overwrite` |
| `assetAdvanced_batch_delete_assets` | 批量删除资产 | `urls[]` |
| `assetAdvanced_validate_asset_references` | 验证资产引用（查找断链） | `directory` |
| `assetAdvanced_get_asset_dependencies` | 获取资产依赖树 | `urlOrUUID`, `direction`(dependents/dependencies/both) |
| `assetAdvanced_get_unused_assets` | 查找未使用的资产 | `directory`, `excludeDirectories[]` |
| `assetAdvanced_compress_textures` | 批量压缩纹理 | `directory`, `format`(auto/jpg/png/webp), `quality`(0.1-1.0) |
| `assetAdvanced_export_asset_manifest` | 导出资产清单 | `directory`, `format`(json/csv/xml), `includeMetadata` |

### 14. Validation — 参数验证工具

| 工具 | 说明 | 关键参数 |
|------|------|----------|
| `validation_validate_json_params` | 验证并修复 JSON 参数 | `jsonString`, `expectedSchema` |
| `validation_safe_string_value` | 生成安全字符串值 | `value` |
| `validation_format_mcp_request` | 格式化 MCP 请求（正确 JSON 转义） | `toolName`, `arguments` |

---

## 常用操作速查

### 创建场景并添加节点

```
1. scene_create_scene → sceneName: "Game", savePath: "db://assets/scenes/Game.scene"
2. scene_open_scene → scenePath: "db://assets/scenes/Game.scene"
3. scene_get_current_scene → 获取场景根节点 UUID
4. node_create_node → name: "Canvas", parentUuid: <根节点UUID>, nodeType: "2DNode"
5. component_attach_script → nodeUuid: <节点UUID>, scriptPath: "db://assets/scripts/core/GameMain.ts"
```

### 资产路径格式

Cocos Creator 使用 `db://assets/...` 格式引用项目内资产：
- 脚本: `db://assets/scripts/core/GameMain.ts`
- 场景: `db://assets/scenes/Game.scene`
- 预制体: `db://assets/resources/prefabs/ColorBall.prefab`
- 纹理: `db://assets/resources/textures/game_atlas.png`
- 配置: `db://assets/resources/configs/levels_config.json`
- 语言包: `db://assets/resources/i18n/zh_cn.json`
