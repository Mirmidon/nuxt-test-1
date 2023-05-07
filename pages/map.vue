<template>
  <div id="cesiumContainer"></div>
</template>

<script setup>
onMounted(() => {
  Cesium.Ion.defaultAccessToken = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiJhZjA3ZjcyZS1mNGNiLTQ4ZDctOWJiZC1hMDA4MDJhMDMzMmYiLCJpZCI6MTc3NjcsInNjb3BlcyI6WyJhc3IiLCJnYyJdLCJpYXQiOjE1NzI3ODUzMTB9.2LicWp6NY55yvDcmuWnZLcozBJa2BB7E07S34bALdNg';

  // Initialize the Cesium Viewer in the HTML element with the `cesiumContainer` ID.
  var viewer = new Cesium.Viewer('cesiumContainer', {
    requestRenderMode: true,
    maximumRenderTimeChange: Infinity,
    timeline: false,
    animation: false,
    baseLayerPicker: false,
    sceneModePicker: false,
    //
    terrainProvider: Cesium.createWorldTerrain(),
    imageryProvider: Cesium.createWorldImagery(), // ~
    terrain: Cesium.Terrain.fromWorldTerrain(),
    // from 4d inno
    // imageryProvider: false, // ?
    geocoder: false,
    fullscreenButton: false,
    homeButton: false,
    navigationHelpButton: false,
    scene3DOnly: false,
    selectionIndicator: false,
    infoBox: false,
  });

  viewer.resolutionScale = 1;

  const positron = new Cesium.UrlTemplateImageryProvider({
    url: 'https://{s}.basemaps.cartocdn.com/light_nolabels/{z}/{x}/{y}{r}.png',
    credit: 'Map tiles by CartoDB, under CC BY 3.0. Data by OpenStreetMap, under ODbL.'
  })
  viewer.imageryLayers.addImageryProvider(positron)

  // Add Cesium OSM Buildings, a global 3D buildings layer.
  viewer.scene.primitives.add(Cesium.createOsmBuildings());
  // viewer.clock.currentTime = Cesium.JulianDate.fromIso8601('2023-05-07T07:23:19.06128571429871954Z');
  viewer.scene.globe.depthTestAgainstTerrain = true;

  viewer.camera.flyTo({
    destination: Cesium.Cartesian3.fromDegrees(48.745, 55.751, 2000), // longitude, latitude, height
    orientation: {
      heading: 0.0,
      pitch: Cesium.Math.toRadians(-90),
      roll: 0.0
    },
    duration: 2
  })
})
</script>