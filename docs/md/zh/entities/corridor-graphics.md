# 走廊

`corridor-graphics` 走廊对象组件，作为`entity`的子组件添加包含走廊对象的实体到场景。走廊对象是一个由中心线和宽度定义的形状，符合地球的曲率。 它可以放置在表面或海拔高度，并可任选地挤压成一个体积，如下面的示例所示。

## 示例

### 添加走廊到场景

#### 预览

<doc-preview>
  <template>
    <div class="viewer">
      <cesium-viewer @ready="ready">
        <entity :name="name1" :description="description" :corridor.sync="corridor1">
          <corridor-graphics :positions="positions1" :material="material1" :width="200000.0"></corridor-graphics>
        </entity>
        <entity :name="name2" :description="description" :corridor.sync="corridor2">
          <corridor-graphics :positions="positions2" :height="100000.0" :width="200000.0" :cornerType="0"
            :material="material2" :outline="true"></corridor-graphics>
        </entity>
        <entity :name="name3" :description="description" :corridor.sync="corridor3">
          <corridor-graphics :positions="positions3" :material="material3" :outlineColor="outlineColor3" :outline="true"
            :height="200000.0" :extrudedHeight="100000.0" :width="200000.0" :cornerType="cornerType3" :outlineColor="outlineColor3"></corridor-graphics>
        </entity>
      </cesium-viewer>
    </div>
  </template>

  <script>
    export default {
      data () {
        return {
          description: 'Hello Vue Cesium',

          corridor1: {},
          name1: 'Red corridor on surface with rounded corners',
          positions1: [],
          material1: {},

          corridor2: {},
          name2: 'Green corridor at height with mitered corners and outline',
          positions2: [],
          cornerType2: 0,
          material2: {},

          corridor3: {},
          name3: 'Blue extruded corridor with beveled corners and outline',
          positions3: [],
          cornerType3: 0,
          material3: {},
          outlineColor3: {}
        }
      },
      methods: {
        ready (cesiumInstance) {
          console.log('CesiumReady')
          const {Cesium, viewer} = cesiumInstance
          this.positions1 = Cesium.Cartesian3.fromDegreesArray([
            100.0, 40.0,
            105.0, 40.0,
            105.0, 35.0
          ])
          this.material1 = Cesium.Color.RED.withAlpha(0.5)

          this.positions2 = Cesium.Cartesian3.fromDegreesArray([
            90.0, 40.0,
            95.0, 40.0,
            95.0, 35.0
          ])
          this.cornerType2 = Cesium.CornerType.MITERED
          this.material2 = Cesium.Color.GREEN

          this.positions3 =  Cesium.Cartesian3.fromDegreesArray([
            80.0, 40.0,
            85.0, 40.0,
            85.0, 35.0
          ])
          this.cornerType3 = Cesium.CornerType.BEVELED,
          this.material3 =  Cesium.Color.BLUE.withAlpha(0.5)
          this.outlineColor3 = Cesium.Color.WHITE
        }
      }
    }
  </script>
</doc-preview>

#### 代码

```html
<template>
  <div class="viewer">
    <cesium-viewer @ready="ready">
      <entity :name="name1" :description="description" :corridor.sync="corridor1">
        <corridor-graphics :positions="positions1" :material="material1" :width="200000.0"></corridor-graphics>
      </entity>
      <entity :name="name2" :description="description" :corridor.sync="corridor2">
        <corridor-graphics :positions="positions2" :height="100000.0" :width="200000.0" :cornerType="0"
          :material="material2" :outline="true"></corridor-graphics>
      </entity>
      <entity :name="name3" :description="description" :corridor.sync="corridor3">
        <corridor-graphics :positions="positions3" :material="material3" :outlineColor="outlineColor3" :outline="true"
          :height="200000.0" :extrudedHeight="100000.0" :width="200000.0" :cornerType="cornerType3" :outlineColor="outlineColor3"></corridor-graphics>
      </entity>
    </cesium-viewer>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        description: 'Hello Vue Cesium',

        corridor1: {},
        name1: 'Red corridor on surface with rounded corners',
        positions1: [],
        material1: {},

        corridor2: {},
        name2: 'Green corridor at height with mitered corners and outline',
        positions2: [],
        cornerType2: 0,
        material2: {},

        corridor3: {},
        name3: 'Blue extruded corridor with beveled corners and outline',
        positions3: [],
        cornerType3: 0,
        material3: {},
        outlineColor3: {}
      }
    },
    methods: {
      ready (cesiumInstance) {
        console.log('CesiumReady')
        const {Cesium, viewer} = cesiumInstance
        this.positions1 = Cesium.Cartesian3.fromDegreesArray([
          100.0, 40.0,
          105.0, 40.0,
          105.0, 35.0
        ])
        this.material1 = Cesium.Color.RED.withAlpha(0.5)

        this.positions2 = Cesium.Cartesian3.fromDegreesArray([
          90.0, 40.0,
          95.0, 40.0,
          95.0, 35.0
        ])
        this.cornerType2 = Cesium.CornerType.MITERED
        this.material2 = Cesium.Color.GREEN

        this.positions3 =  Cesium.Cartesian3.fromDegreesArray([
          80.0, 40.0,
          85.0, 40.0,
          85.0, 35.0
        ])
        this.cornerType3 = Cesium.CornerType.BEVELED,
        this.material3 =  Cesium.Color.BLUE.withAlpha(0.5)
        this.outlineColor3 = Cesium.Color.WHITE
      }
    }
  }
</script>
```

## 属性

参考官方文档 [CorridorGraphics](https://cesiumjs.org/Cesium/Build/Documentation/CorridorGraphics.html)
<!-- |属性名|类型|默认值|描述|
|------|-----|-----|----|
|positions|Property||`optional` 指定表示线条的Cartesian3位置数组。|
|followSurface|Property|true|`optional` 指定线段是弧线还是直线连接。|
|clampToGround|Property|false|`optional` 指定线是否贴地。|
|width|Property|1.0|`optional` 指定线的宽度（像素）。|
|show|Property|true|`optional` 指定线是否可显示。|
|material|MaterialProperty|Color.WHITE|`optional` 指定用于绘制线的材质。|
|depthFailMaterial|MaterialProperty||`optional` 指定用于绘制低于地形的线的材质。|
|granularity|Property|Cesium.Math.RADIANS_PER_DEGREE|`optional`指定每个纬度和经度之间的角距离，当followSurface为true时有效。|
|shadows|Property|ShadowMode.DISABLED|`optional` 指定这些是否投射或接收来自每个光源的阴影。|
|distanceDisplayCondition|Property||`optional` 指定相机到线的距离。|
|zIndex|Property|0|`optional` 指定用于排序地面几何的zIndex。 仅当`clampToGround`为真且支持地形上的折线时才有效。|
--- -->

## 事件

|事件名|参数|描述|
|------|----|----|
|ready|{Cesium, viewer}|该组件渲染完毕时触发，返回Cesium类, viewer实例。|
|definitionChanged||每当更改或修改属性或子属性时触发该事件。|
