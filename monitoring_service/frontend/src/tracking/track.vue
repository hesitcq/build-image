/*
 *  Copyright 2020 Huawei Technologies Co., Ltd.
 *
 *  Licensed under the Apache License, Version 2.0 (the "License");
 *  you may not use this file except in compliance with the License.
 *  You may obtain a copy of the License at
 *
 *      http://www.apache.org/licenses/LICENSE-2.0
 *
 *  Unless required by applicable law or agreed to in writing, software
 *  distributed under the License is distributed on an "AS IS" BASIS,
 *  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 *  See the License for the specific language governing permissions and
 *  limitations under the License.
 */
<template>
  <div
    id="app"
    class="track-container"
  >
    <persons />
    <cameras />
  </div>
</template>
<script lang="js">
import persons from './persons.vue'
import cameras from './cameras.vue'

export default {
  name: 'Track',
  props: [],
  components: {
    'persons': persons,
    'cameras': cameras
  },
  data () {
    return {
    }
  },
  methods: {

  }
}
</script>

<style scoped lang="less">
 .track-container {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin-top: 64px;
  // background-image: url("../assets/images/home.png");
  //  background-image: linear-gradient(to right, #650675, #115286, #F0F3FA);
  background-image: linear-gradient(to right, #650675, #115286, #6d727d);
  max-height: 100vh;
  overflow: auto;
  // opacity: 0.85;
}
@media(max-width:767.98px) {
  .track-container{
    background: none
  }
}
</style>
