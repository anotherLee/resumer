<template xmlns:v-bind="http://www.w3.org/1999/xhtml">
  <div id="resumerEditor">
      <ol class="icons">
        <li v-for="(item,index) in 6" v-bind:class="{active: currentTab===index}" @click="currentTab=index">
          <svg class="icon" aria-hidden="true"> <use v-bind:xlink:href="`#icon-${icons[index]}`"></use></svg>
        </li>

      </ol>

    <div class="edit">
      <ul class="panes">
        <li v-bind:class="{active:currentTab===0}">
          <h2>个人信息</h2>
          <el-form>
            <el-form-item label="姓名">
              <el-input v-model="resumer.profile.name"></el-input>
            </el-form-item>
            <el-form-item label="城市">
              <el-input v-model="resumer.profile.city"></el-input>
            </el-form-item>
            <el-form-item label="出生年月">
              <el-input v-model="resumer.profile.birth"></el-input>
            </el-form-item>
          </el-form>
        </li>
        <li v-bind:class="{active:currentTab===1}">
          <ArrayEditor v-bind:items="resumer.workHistory" v-bind:labels="{company:'公司',content:'工作内容'}" title="工作经历" v-bind:content="{company:'',content:''}"></ArrayEditor>

        </li>
        <li v-bind:class="{active:currentTab===2}">
          <ArrayEditor v-bind:items="resumer.studyHistory" v-bind:labels="{school:'学校',duration:'时间',degree:'学位'}" title="学习经历" v-bind:content="{school:'',duration:'',degree:''}"></ArrayEditor>

        </li>
        <li v-bind:class="{active:currentTab===3}">
          <ArrayEditor v-bind:items="resumer.projects" v-bind:labels="{name:'项目名称',content:'项目内容'}" title="项目经历" v-bind:content="{name:'',content:''}"></ArrayEditor>

        </li>
        <li v-bind:class="{active:currentTab===4}">
          <ArrayEditor v-bind:items="resumer.awards" v-bind:labels="{time:'获奖时间',content:'奖励内容'}" title="获奖" v-bind:content="{time:'',content:''}"></ArrayEditor>
        </li>
        <li v-bind:class="{active:currentTab===5}">
          <h2>联系方式</h2>
          <el-form>
            <el-form-item label="QQ">
              <el-input v-model="resumer.contacts.qq"></el-input>
            </el-form-item>
            <el-form-item label="邮箱">
              <el-input v-model="resumer.contacts.email"></el-input>
            </el-form-item>
            <el-form-item label="手机">
              <el-input v-model="resumer.contacts.telephone"></el-input>
            </el-form-item>
          </el-form>
        </li>
      </ul>
    </div>
  </div>
</template>


<script>
  import ArrayEditor from './ArrayEditor.vue'
  export default{
    props:['resumer'],
    data(){
      return {
        currentTab:0,
        icons:['shenfen','work','study','gz','jiangli','Telephone2'],
//        profile:{ name:'', city:'', birth:'' },
//        workHistory:[{company:'',content:'' }],
//        studyHistory:[{school:'',duration:'',degree:''}],
//        projects:[{name:'',content:''}],
//        awards:[{time:'',content:''}],
//        contacts:{qq:'',email:'',telephone:''},
//        addData:[{ name:'', city:'', birth:'' },{company:'',content:'' },{school:'',duration:'',degree:''},{name:'',content:''},{time:'',content:''}]

      }
    },
    methods:{

    },
    components:{
      ArrayEditor
    }
  }
</script>


<style lang="scss">
  @mixin border{
    border:1px solid #ddd;
    border-radius:5px;
  }
  #resumerEditor{
    display:flex;
    justify-content:space-between;

    .icons{
      width: 60px; height: 100%; padding-top: 60px; background: white;
      display: flex; align-items: center; flex-direction: column;

      li{
        border:1px solid #ddd;
        .icon{
          width:60px; height:60px;
          fill:#999999; padding:10px; cursor:pointer;
        }

      }
      li.active > .icon{
        fill:#3789E0;
      }
    }

    .edit{
      @include border; width:50%;
      margin:60px 40px 60px 0; background:white;
      box-shadow:0 0 10px #ddd; overflow:auto;
      .panes{

        li{
          display:none; padding: 50px 50px 0 50px;
          overflow:auto;

          h2{
            padding-bottom:20px;
          }

          #form {

            div {
              position: relative;

              #delete {
                position: absolute;
                right: 0;
                top: 0;
                display: none;
                z-index: 1;
              }

            }
            div:hover > #delete {
              display: block;
            }

          }
        }

        li.active{
          display:block;
        }
      }
    }
  }
</style>
