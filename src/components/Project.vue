<template>
  <div class="row mb-4">
    <div class=" project col-12  shadow" data-toggle="modal" data-target="#projectModal" @click="setProject">
      <div class="row">
        <div class="col-6 p-0 cover-img">
          <img :src="project.imgUrl" class="img-fluid" />
        </div>
        <div class="col-6">
          <div class="row p-0 pictures">
            <div v-for="(photo, i) in project.photos" :key="'photo-'+i" class="col-6 secondImg" :style="'background-image: url('+photo.imgUrl+')'"></div>
          </div>
          <div class="row justify-content-center align-items-center  project-title">
            <div class="border p-2">
              {{ project.title }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { AppState } from '../AppState'
import { computed, reactive, onMounted } from 'vue'
import { projectService } from '../services/ProjectService'
export default {
  props: { project: { type: Object, required: true } },
  name: 'Project',
  setup(props) {
    const state = reactive({

    })
    return {
      state,
      setProject() {
        projectService.setProject(props.project.id)
      }
    }
  }
}
</script>

<style lang='scss' scoped>

.project{
  transition: all .1s linear;
  height: 13em;
  overflow: hidden;
}

.project:hover{
  outline: solid 1px var(--light);
  transform: scale(1.075);
  box-shadow: 0px 8px 6px 0px rgba(0, 0, 0, 0.4);
}

.pictures{
  height: 100%;
  overflow: hidden;
}

.secondImg{
  min-height: 5em;
  background-size: cover;
}

.cover-img{
  overflow: hidden;
  > img{
    height: auto;
    width: 100%;
  }
}
.project-title{
  background: #00000048;
  position: absolute;
  top: 0;
  width: 100%;
  height: 13em;
}

</style>
