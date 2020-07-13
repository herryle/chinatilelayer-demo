<template>
  <div id="app">
    <div style="z-index:999;  position:absolute; right:100px;top:30px">
      <el-select v-model="value" placeholder="请选择地图" @change="changeLayer">
        <el-option-group
          v-for="group in options1"
          :key="group.label"
          :label="group.label"
        >
          <el-option
            v-for="item in group.options2"
            :key="item.value"
            :label="item.label"
            :value="item.value"
          ></el-option>
        </el-option-group>
      </el-select>
    </div>
    <l-map style="height: 100vh;" :zoom="zoom" :center="center">
      <l-china-tilelayer :layerName="layerName" :options="options" />
    </l-map>
  </div>
</template>

<script>
import 'leaflet/dist/leaflet.css'
import { LMap } from 'vue2-leaflet'
import LChinaTilelayer from 'vue2-leaflet-chinatilelayer'

export default {
  components: { LMap, LChinaTilelayer },
  data() {
    return {
      zoom: 13,
      layerName: 'Geoq.Normal.PurplishBlue',
      options: {
        maxZoom: 18,
        minZoom: 9,
        key: '7da7ea4ab0d3846f0755c771291a3240',
      },
      center: [32.06031863553111, 118.76315116882326],
      options1: [
        {
          label: 'TianDiTu',
          options2: [
            {
              value: 'TianDiTu.Normal.Map',
              label: 'TianDiTu.Normal.Map',
            },
            {
              value: 'TianDiTu.Terrain.Map',
              label: 'TianDiTu.Terrain.Map',
            },
            {
              value: 'TianDiTu.Satellite.Map',
              label: 'TianDiTu.Satellite.Map',
            },
          ],
        },
        {
          label: 'GaoDe',
          options2: [
            {
              value: 'GaoDe.Normal.Map',
              label: 'GaoDe.Normal.Map',
            },
            {
              value: 'GaoDe.Satellite.Map',
              label: 'GaoDe.Satellite.Annotion',
            },
          ],
        },
        {
          label: 'Geoq',
          options2: [
            {
              value: 'Geoq.Normal.Map',
              label: 'Geoq.Normal.Map',
            },
            {
              value: 'Geoq.Normal.PurplishBlue',
              label: 'Geoq.Normal.PurplishBlue',
            },
            {
              value: 'Geoq.Normal.Gray',
              label: 'Geoq.Normal.Gray',
            },
            {
              value: 'Geoq.Normal.Warm',
              label: 'Geoq.Normal.Warm',
            },
            {
              value: 'Geoq.Normal.Hydro',
              label: 'Geoq.Normal.Hydro',
            },
          ],
        },
        {
          label: 'OSM',
          options2: [
            {
              value: 'OSM.Normal.Map',
              label: 'OSM.Normal.Map',
            },
          ],
        },
      ],
      value: '',
    }
  },
  methods: {
    changeLayer(e) {
      this.layerName = e
    },
  },
}
</script>

<style>
body {
  margin: 0px;
}
</style>
