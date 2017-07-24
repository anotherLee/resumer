<template>
  <div class="page">
    <header>
      <Topbar v-on:preview="preview" v-on:edit="edit" id="topbar" v-bind:previewMode="previewMode" v-bind:classChange="classChange"></Topbar>
    </header>

    <main>
      <ResumerEditor id="resumerEditor" v-bind:resumer="resumer" v-if="previewMode===false"></ResumerEditor>
      <ResumerPreview class="resumerPreview" v-bind:resumer="resumer" v-bind:class="{previewMode:previewMode===true}"></ResumerPreview>
    </main>
    <el-button class="exitPreview" v-if="previewMode===true" v-on:click="exitPreview">退出预览</el-button>
  </div>
</template>


<script>
import 'normalize.css/normalize.css'
import './assets/reset.css'

import Topbar from './components/Topbar.vue'
import ResumerEditor from './components/ResumerEditor.vue'
import ResumerPreview from './components/ResumerPreview.vue'


export default {
  name: 'app',
  data: function () {
    return {
      resumer:{
        profile:{ name:'', city:'', birth:'' },
        workHistory:[{company:'',content:'' }],
        studyHistory:[{school:'',duration:'',degree:''}],
        projects:[{name:'',content:''}],
        awards:[{time:'',content:''}],
        contacts:{qq:'',email:'',telephone:''}
      },
      previewMode:false,
      classChange:true
    }
  },
  components:{ Topbar, ResumerEditor, ResumerPreview },
  methods:{
    preview(){
      this.previewMode = true
      this.classChange = false
    },
    edit(){
      this.previewMode = false
      this.classChange = true
    },
    exitPreview(){
      this.previewMode = false
      this.classChange = true
    }
  }
}
</script>

<style lang="scss">
  @mixin border{
    border:1px solid #ddd; box-shadow:0 0 5px #eee;
  }
  .page,body,html{ height:100%; }
  .page{

    display:flex; flex-direction:column;

    header{

      #topbar{
        height:60px;
        @include border; border-radius:0px;
      }
    }
    main{
      display:flex; background:#EEEEEE; flex-grow:1; margin-top:-2px;

      #resumerEditor{
        @include border; flex:1;
      }
      #resumerPreview{
        @include border; flex:1;
      }
      .previewMode{ border:1px solid red;
        .preview{ margin:40px auto 40px !important; width:50% !important;

        }
      }

    }
    .exitPreview{ position:fixed; right:100px; bottom:40px; color:red;

    }


  }

</style>
