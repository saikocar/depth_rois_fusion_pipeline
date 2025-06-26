# depth\_rois\_fusion\_pipeline

## 概要

`depth_rois_fusion_pipeline` は、カメラのROIと深度情報をフュージョンしてyoloベースで対象の物体までの距離を推定し、物体が走行予定のLane上に存在するか確認し、検出オブジェクトの空間的・意味的条件によるフィルタリングを確認する一連のノードを起動するROS 2 launchパッケージです。

本パイプラインは以下のノードで構成されます：

1. **depth\_rois\_fusion\_node**（`depth_rois_fusion` パッケージ）:

   * カメラ画像のROIと点群から得られた深度情報をフュージョンします。

2. **object\_on\_lanelet\_checker\_node**（`object_on_lanelet_checker` パッケージ）:

   * オブジェクトがルート上のLanelet内に存在するかを確認します。

3. **object\_filter\_node**（`objects_filter` パッケージ）:

   * セマンティックラベルや空間条件に基づいてオブジェクトをフィルタリングし、オブジェクトのメッセージ及び可視化用のマーカーを出力します。

### 使用方法

以下のコマンドでパイプラインを起動できます：

```bash
ros2 launch depth_rois_fusion_pipeline depth_rois_fusion_pipeline.launch.py
```

### 設定ファイル

各ノードのパラメータは以下のように YAML ファイルから読み込まれます：

```yaml
# config/config.yaml

depth_rois_fusion_node:
  ros__parameters:
    ...

object_on_lanelet_checker_node:
  ros__parameters:
    ...

object_filter_node:
  ros__parameters:
    ...
```

各ノードは、対応するセクションの `ros__parameters` を読み込んで動作します。

## 依存パッケージ

このパッケージを使用するには、以下のパッケージがインストールされビルドされている必要があります：

* `depth_rois_fusion`
* `object_on_lanelet_checker`
* `objects_filter`
