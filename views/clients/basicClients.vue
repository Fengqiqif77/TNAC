<template>
  <div>
    <div class="operate" >
      <a-button type="primary" style="margin-top:50px;margin-left:90%;width: 100px" icon="plus" @click="add">
        添加
      </a-button>
    </div>
    <a-card
      style="margin-top: 24px"
      :bordered="false"
    >
      <span slot="title" class="number-text">
        259位活跃用户中的32位
      </span>
      <div slot="extra">
        <a-input style="margin-right: 16px; width: 272px;" >
          <a-icon slot="prefix" type="search" style="color:#55c2c2" />
        </a-input>
        <a-radio-group defaultValue="a">
          <a-radio-button value="a">全部客户</a-radio-button>
          <a-radio-button value="b">活跃客户</a-radio-button>
          <a-radio-button value="c">不活跃用户</a-radio-button>
        </a-radio-group>
      </div>
      <a-row class="members">
        <a-row>
          <a-col :xs="12" :sm="6" :md="3" v-for="(item, index) in clientsList" :key="index">
            <a >
              <a-avatar style="width:60px;height:60px" size="large" :src="item.avatar"/>
              <p style="margin-top:10px" class="member">{{ item.name }}</p>
            </a>
          </a-col>
        </a-row>
      </a-row>
    </a-card>
  </div>
</template>

<script>
export default {
    components: {
       name: 'Clients'
    },
    data () {
        return {
            clientsList: []
        }
    },
    mounted () {
    this.getClients()
    },
    methods: {
    getClients () {
      this.$http.get('/workplace/teams').then(res => {
        this.clientsList = res.result
      })
    }
    }
}
</script>

<style>
.number-text{
  font-size: 15px;
}
</style>
