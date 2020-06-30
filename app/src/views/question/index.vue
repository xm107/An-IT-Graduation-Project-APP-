<template>
  <div v-if="loading">
    <!-- 简单填充下内容 -->
    <div class="split"></div>
    <van-skeleton title avatar :row="4" v-for="item in 4" :key="item" />
  </div>
  <div v-else style=" overflow-y:auto; overflow-x:auto; width:100%; height:100%;">
    <div class="all" v-for="item in list" :key="item.id">
      <div class="left">
        <img :src="userInfo.photo" />
      </div>
      <div class="right">
        <div>{{userInfo.name}}</div>
        <div class="question">{{item.question}}</div>
      </div>
    </div>
  </div>
</template>
<script>
import { getUserInfo } from '@/api/user'

export default {
  data () {
    return {
      userInfo: {},
      list: [
        {
          id: 1,
          question: '你好么?'
        },
        {
          id: 2,
          question: 'IT行业今后的发展你怎么看？？'
        },
        {
          id: 3,
          question: '目前疫情对IT行业的影响你怎么看'
        },
        {
          id: 4,
          question: '测试提问1？'
        },
        {
          id: 5,
          question: '测试提问2？'
        },
        {
          id: 6,
          question: '测试提问3？'
        },
        {
          id: 7,

          question: '测试提问4？'
        },
        {
          id: 8,
          question: '测试提问5？'
        },
        {
          id: 9,
          question: '测试提问6？'
        },
        {
          id: 10,
          question: '测试提问7？'
        },
        {
          id: 11,
          question: '测试提问8？'
        },
        {
          id: 12,
          question: '测试提问9？'
        },
        {
          id: 13,
          question: '测试提问10？'
        },
        {
          id: 14,
          question: '测试提问11？'
        }
      ],
      loading: true
    }
  },
  mounted () {
    setTimeout(
      function () {
        this.loading = false
      }.bind(this),
      500
    )
  },
  methods: {
    // 获取用户的个人信息
    async getUserInfo () {
      this.userInfo = await getUserInfo()
      // 获取了用户信息
      this.updatePhoto({ photo: this.userInfo.photo }) // 调用mutation来设置头像
    }
  },
  created () {
    this.getUserInfo() // 获取用户信息
  }
}
</script>
<style lang="less" scoped>
.all {
  .left {
    margin: 20px 10px 0 15px;
    img {
      width: 40px;
      height: 40px;
      border-radius: 50%;
    }
  }
  .right {
    margin-top: 30px;
    .question {
      margin-top: 10px;
    }
  }
  display: flex;
}
</style>
