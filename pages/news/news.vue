<template>
	<view class="content">
		<view class="top-bar">
			<view class="top-bar-left">
				通知公告
				<text class="top-title">新闻资讯</text>
				广告天地
			</view>
			<view class="top-bar-right">
				<view class="add"> <image src="../../static/add.png"></image> </view>
				<view class="search"> <image src="../../static/search.png"></image> </view>
			</view>
		</view>
		<view class="main">
			<view class="news">
				<view class="news_item" @tap="onClick(news)" v-for="news in newsList">
					<view class="news_item_l">
						<text class="tip">1</text>
						<image :src="news.image"></image>
					</view>
					<view class="news_item_r">
						<view class="upper">
							<view class="name">{{news.title}}</view>
							<view class="time">{{news.time}}</view>
						</view>
						<view class="person">发布人：所念皆星河</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>

export default {
	data() {
		return{
			newsList:[
				{"title":"校长熊继军到招生录取现场","image":"../../static/iocn/news-detail1.jpg","time":"8月05日","content":"8月5日下午，校长熊继军一行到招生录取现场慰问并调研本科招生工作。招就处处长李博详细汇报了今年各省的招生情况。截止目前，我校已高质量且顺利完成31个省市自治区的全部本科招生任务，生源质量明显好于去年，共计录取8896人。录取通知书即将全部寄出。熊继军要求，要认真总结今年的招生情况，切实做好数据统计与分析，同时认真总结近几年招生工作的开展情况，为下一步更好地开展工作提供借鉴与支撑。他同时对暑期坚守岗位的工作人员表示亲切慰问，希望大家再接再厉，给今年的招生录取工作画上圆满的句号。"},
				{"title":"我校与大同市新荣区签署省校合作框架协议","image":"../../static/iocn/news-detail2.jpg","time":"8月06日","content":"8月4日，我校与大同市新荣区深化省校合作共建“12大基地”签约仪式在云冈建国宾馆举行。此次合作签约，既是落实省委、省政府关于“深化省校合作、共建12大基地”部署要求，也是双方深化合作、共谋发展的重要成果，开启了双方深化合作、互利互惠、共谋发展的新篇章。校长熊继军，大同市委常委、组织部部长崔巍，市政府副市长马安全，市政府秘书长庞君，大同市新荣区委书记邓志蓉等见签，我校副校长苏铁熊、新荣区委常委、副区长刘玉巍代表双方签署省校合作框架协议。"},
				{"title":"我校8项科技成果荣获山西省科学技术奖","image":"../../static/iocn/news-detail5.jpg","time":"8月4日","content":"近日，山西省政府印发《关于2020年度山西省科学技术奖励的决定》，对促进我省科学技术进步和经济社会发展作出突出贡献的科学技术人员和组织给予奖励，共授予19个项目一等奖、85个项目二等奖、89个项目三等奖，10家企业获“企业技术创新奖”。本年度我校共获奖8项，其中技术发明一等奖1项、自然科学二等奖4项、技术发明二等奖2项、科技进步三等奖（参与）1项。2020年度省科学技术奖突出转型发展政策导向，突出科技成果应用导向，突出企业技术创新主体地位，突出科技前沿和自主创新，鼓励和引导全省科学技术工作者自觉肩负起历史赋予的科技创新重任，着力攻克“卡脖子”关键核心技术，努力形成一批标志性重大科技成果，为我省创新驱动高质量转型发展作出了新的更大贡献。近年来，我校以冲击“双一流”为目标，坚持“面向科技前沿，面向行业企业；重视基础研究，重视成果转化”的工作思路，推进落实《中北大学科技振兴行动计划》，科研成果产出趋好。"},
			],
			
		}
	},
	methods: {
		onClick(news) {
			uni.navigateTo({url: "news_details?news=" + JSON.stringify(news)})
		}
	}
}
</script>

<style lang="scss">
	.content{
		display: flex;
		flex-direction: column;
		//align-items: center;
		justify-content: center;
	}
	.top-bar{
		position: fixed;
		z-index: 1001;
		top: 0;
		left: 0;
		width: 100%;
		height: 70rpx;
		box-sizing: border-box;
		background-color: white;
		box-shadow: 0rpx 1rpx 0rpx 0rpx rgba(0,0,0,0.1);
		padding-left: 32rpx;
		padding-right: 32rpx;
		.top-bar-left{
			float:left;
			margin-top: 10rpx;
			margin: 10rpx;
			font-weight:540;
			width: auto;
			.top-title{
				color: rgba(255,93,91,1);
				margin-left: 30rpx;
				margin-right: 30rpx;
			}
		}
		.top-bar-right{
			float: right;
			.search{
				width: 30rpx;
				height: 30rpx;
				display: inline-block;
				margin-right: 20rpx;
			}
			.add{
				width: 30rpx;
				height: 30rpx;
				display: inline-block;
				margin-right: 45rpx;
			}
			image{
				padding: 10rpx 0 0 10rpx;
				width: 52rpx;
				height: 52rpx;
			}
		}
	}
	.main{
		padding: 70rpx 32rpx 0;
	}
	.news{
		width: 100%;
		.news_item{
		height: 96rpx;
		padding: 16rpx 0;
		border-bottom: 1rpx solid #F1F1F1;
		.news_item_l{
			position:relative;
			float: left;
			image{
				width: 96rpx;
			 	height: 96rpx;
				border-radius: 50%;
			}
			.tip{
				position: absolute;
				z-index: 100;
				top: -6rpx;
				left: 68rpx;
				min-width: 36rpx;
				height: 36rpx;
				background: rgba(255,93,91,1);
				border-radius: 18rpx;
				line-height: 36rpx;
				text-align: center;
				color: white;
			}
		}
		.news_item_r{
			padding-left: 128rpx;
			//width: 100%;
			.upper{
				height: 50rpx;
				.name{
					float: left;
					font-size: 28rpx;
					font-weight: 400;
					//color:rgba(39,40,50,1);
					font-weight:540;
					line-height: 50rpx;
				}
				.time{
					float: right;
					font-size: 24rpx;
					color: rgba(39,40,50,0.6);
					line-height: 50rpx;
				}
			}
		}
		.person{
			font-size: 24rpx;
			color: rgba(39,40,50,0.6);
			line-height: 40rpx;
		}
	 }
    }

</style>
