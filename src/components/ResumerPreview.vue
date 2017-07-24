<template>
  <div id="resumerPreview">
    <div class="preview">
      <section class="profile" v-show="resumer.profile.name !== '' || resumer.profile.city !== '' || resumer.profile.birth !== '' ">
        <h1>
          {{resumer.profile.name || '请填写姓名'}}
        </h1>
        <p>
          {{resumer.profile.city || '请填写城市'}} | {{resumer.profile.birth || '请填写出生年月'}}
        </p>
      </section>

      <section v-if="filter(resumer.workHistory).length > 0" class="workHistory">
        <h2>工作经历</h2>
        <hr/>
        <ul v-for="item in filter(resumer.workHistory)">
          <li>{{item.company}}</li>
          <li> {{item.content}}</li>
        </ul>
      </section>
      <section v-if="filter(resumer.studyHistory).length > 0" class="studyHistory">
        <h2>学习经历</h2>
        <hr/>
        <ul v-for="item in filter(resumer.studyHistory)">
          <li>{{item.school}}</li>
          <li>{{item.duration}}</li>
          <li>{{item.degree}}</li>
        </ul>
      </section>
      <section v-if="filter(resumer.projects).length > 0" class="projects">
        <h2>项目经历</h2>
        <hr/>
        <ul v-for="item in filter(resumer.projects)">
          <li>{{item.name}}</li>
          <li>{{item.content}}</li>
        </ul>
      </section>
      <section v-if="filter(resumer.awards).length > 0" class="awards">
        <h2>获得奖励</h2>
        <hr/>
        <ul v-for="item in filter(resumer.awards)">
          <li >
            <li>{{item.time}}</li>
            <li>{{item.content}}</li>
          </li>
        </ul>
      </section>
      <section class="contacts" v-show="resumer.contacts.qq !=='' || resumer.contacts.email !== '' || resumer.contacts.telephone !== '' ">
        <h2>联系方式</h2>
        <hr/>
        <ul>
          <li>QQ:{{resumer.contacts.qq}}</li>
          <li>邮箱：{{resumer.contacts.email}}</li>
          <li>手机：{{resumer.contacts.telephone}}</li>
        </ul>
      </section>
    </div>
  </div>
</template>


<script>
  export default{
    props:['resumer'],
    methods:{
      filter:function(array){
        return array.filter((item) =>  this.isEmpty(item))
      },
      isEmpty(object){
        let empty = false
        for(let key in object) {
          if (object[key]) {
            empty = true
            break
          }
        }
        return empty
      }

    }

  }
</script>

<style lang="scss">
  @mixin border{ border:1px solid #ddd; box-shadow:0 0 10px #ddd; }
  @mixin li{ padding:10px 0 0 30px; font-size:16px; }

  #resumerPreview{
    background:#eee; display:flex;
    .preview{
      width:70%; margin:60px 0 60px 40px; @include border;
      background:white; border-radius:5px; padding:40px; overflow:auto;

      .profile{
        padding:15px 0;
      }
      .workHistory{
        padding:15px 0;

        li{
          @include li;
        }
        li:nth-child(1){
          padding:20px 0 0 30px; font-size:19px;
        }
      }
      .studyHistory{
        padding:15px 0;

        li{
          @include li;
        }
        li:nth-child(1){
          padding:20px 0 0 30px; font-size:19px;
        }
      }
      .projects{
        padding:15px 0;

        li{
          @include li;
        }
        ul>li:nth-child(1){
          padding:20px 0 0 30px; font-size:19px;
        }
      }
      .awards{
        padding:15px 0;

        li{
          @include li;
        }
        li:nth-child(1){
          padding:20px 0 0 30px; font-size:19px;
        }
      }
      .contacts{
        padding:15px 0;

        li{
          @include li;
        }
        li:nth-child(1){
          padding:20px 0 0 30px;
        }
      }
    }
  }
</style>
