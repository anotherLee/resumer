<template xmlns:v-bind="http://www.w3.org/1999/xhtml" xmlns: xmlns:v-on="http://www.w3.org/1999/xhtml">
  <div id="topbar">
    <img src="https://i.loli.net/2017/07/19/596f7bb8b2675.png" alt=""/>
    <p class="edit">
      <span @click="edit" v-bind:class="{active:classChange===true}">编辑</span>
      <span @click="preview" v-bind:class="{active:classChange===false}">预览</span>
    </p>
    <p class="save">
      <button @click="save">保存</button>
      <button>退出</button>
    </p>
  </div>
</template>


<script>
  export default{
    props:['previewMode','classChange'],
    data(){
      return {
//        changeClass:true
      }
    },
    methods:{
      preview(){
        this.$emit('preview')
      },
      edit(){
        this.$emit('edit')
      }
    },
    save(){
      this.$emit('save')
    }
  }
</script>

<style lang="scss">
  @mixin border{
    border:1px solid #eee;
  }
  #topbar{
    img{
      height:60px; width:60px; border-right:1px solid #eee; padding:15px; float:left;
      cursor:pointer;
    }
    .edit{
      float:left;

      span{
        display:block; padding:20px 0 0 13px; float:left;
        width:60px; height:60px; border:1px solid #eee;
        color:#B9B9B9; cursor:pointer;
      }
      span.active{
        color:#3789E0;
      }
    }
    .save{
      float:right; margin-right:100px;

      button{
        width:80px; height:30px; margin:15px 10px;
        border:1px solid #59A3E7; background:transparent;
        border-radius:5px; color:#59A3E7; cursor:pointer;
      }
      button:focus{
        outline:none;
      }
      button:active{
        background:#59A3E7;
        color:white;
      }

  }
  }
</style>
