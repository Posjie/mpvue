<template>
   <div>
		 {{msg}}
		 <ul class="list">
			 <li v-for="(item,key) in list" :key="key"  @click="goContent(item.aid)">
			 {{item.title}}
			 </li>
		 </ul>
	 </div>
</template>

<script>

export default {
  data () {
    return {
				msg:'这是新闻页面',
				list:[]
      }
    },
		methods:{
			
			requestData(){
				var that = this;
				var api = 'http://www.phonegap100.com/appapi.php';
				wx.request({
					url: api, // 仅为示例，并非真实的接口地址
					data: {
						a: 'getPortalList' ,
            catid: '20',
            page:'1'
					},
					header: {
						'content-type': 'application/json' // 默认值
					},
					success(res) {
						// console.log(res.data)
						that.list = res.data.result;
					}
				})
			},
			goContent(aid){
					const url = '../newscontent/main?aid='+aid;
				  wx.navigateTo({ url });
			
			}
		},
		created() {
			this.requestData()
		}
  }

</script>

<style scoped>
  .list{
		padding: 5px;
	}
	.list li{

        height: 40px;
        line-height: 40px;
        border-bottom:  1px solid #eee;
        overflow: hidden;
    }
</style>
