<template>
<view>
	
<!--
<view class="nav-wrap">
    <view class="nav-title">汇学</view>
    <view style="display: flex; justify-content: space-around;flex-direction: column;height:100%;">
        <navigator hoverClass="none" url="">
            <view class="nav-capsule">
                <view>
                    <image class="back-pre" src="../../static/logo.png" style="height:35px;width:35px;"></image>
                </view>
            </view>
        </navigator>
    </view>
</view>
-->

<view>
    <!-- 轮播图 -->
    <view class="bbs-swiper-container">
        <swiper class="bbs-swiper" autoplay="true" circular="true" 
            interval="3000" easing-function="easeOutCubic" 
            :current="swiperCurrent" 
            bindchange="swiperChange">
            <!-- 轮播图图片 -->
            <swiper-item class="bbs-swiper-item" v-for="item in rotationList">
            <!-- 加上widthFix可以使图片自适应 -->
            <image :src="item"></image>
            </swiper-item>
        </swiper>
        <!-- 定制轮播图dots -->
		
		
        <view class="bbs-dots">
            <block v-for="index of rotationList.length" key="index">
            <view class="  index == swiperCurrent ? 'bbs-dots-item bbs-dot-active' : 'bbs-dots-item' "></view>
            </block>
        </view>
		
		
    </view>

    <view class="mess_sort">
        <!-- 实时留言 -->
        <view class="leave-message">
            <image class="message-image" src="../../static/sort/message.png"></image>
            <swiper class="swiper_message" circular vertical autoplay interval="5000" easing-function="easeInOutCubic" >
                <swiper-item class="swiper-item-message">
                    <view class="message">
                        
                        <text class="message-name">匿名用户</text>
                        <text class="message-content">寻找一起学习的小伙伴</text>
                    </view>
                </swiper-item>
                <swiper-item class="swiper-item-message">
                    <view class="message">
                        <!-- <image class="message-image" src="../../assets/images/sort/love-mood.png"></image> -->
                        <text class="message-name">所念皆星河</text>
                        <text class="message-content">靠近光、追随光、成为光、发散光。</text>
                    </view>
                </swiper-item>
            </swiper>
        </view>
        


        <!-- 分类标签 -->
        <scroll-view scroll-x class="sort-nav" scroll-with-animation enable-flex="true">
            <view class="sort-nav-item" v-for="item in sortList"  key="index">
                <image class="sort-nav-icon" :src="item.icon" mode="widthFix" lazy-load="false"></image>
                <text class="sort-nav-text">{{item.text}}</text>
                <image class="down-selected"src="../../static/sort/dwon.png"></image>
            </view>
        </scroll-view>   
    </view>
    


    <!-- 分类具体的内容 -->
    <view class="sort-content">
        <block v-for="index of 5" :key="index" > 
            <view class="sort-content-item">
                <view class="sort-content-top" >
                    <!-- 用户信息（头像、用户名等） -->
                    <view class="user-info">
                        <view class="user-photo">
                            <image src="../../static/anonymous.png" mode="widthFix"></image>
                        </view>
                        <view class="user-detail">
                            <view class="user-name">
                                <text>匿名用户</text>
                            </view>
                            <view class="user-flag">
                                <view class="article-sort">闲置交易</view>
                                <view class="user-sex">小姐姐</view>
                                <view class="user-level">Lv20</view>
                            </view>
                        </view>
                        <view class="post-detail">
                            <view class="handle">
                                <image src="../../static/more.png"></image>
                            </view>
                            <view class="post-time">
                                <text>2020-08-28 08:30</text>
                            </view>
                            
                        </view>
                    </view>
                </view>
                <!-- 帖子内容 -->
                <view class="sort-content-middle">
                    <view class="acticle-text">
                        <text>点点繁星挂在苍穹之上，星光泻下落在了人们头上，他们带着星光在太行山上勇敢投身，危难过后这个民族浴火重生。</text>
                    </view>
                    <view class="acticle-image">
                        <block v-for="item in testImage" key="index">
                            <view class="show-image">
                                <image :src="item" mode="aspectfill"></image>
                            </view>
                        </block>
                    </view>
                </view>
                <view class="sort-content-bottom">
                    <view class="like">
                        <image src="../../static/unlike.png" class="bottom-img"></image>
                        <text class="num">99</text>
                    </view>
                    <view class="comment">
                        <image src="../../static/comment.png" class="bottom-img"></image>
                        <text class="num">99</text>
                    </view>
                    
                </view>
            </view>
        </block>
    </view>
</view>

</view>
</template>

<script>
export default {
	data() {
		return{
			navH: 0,
			
			//轮播图
			rotationList:[
			  '../../static/iocn/news-detail1.jpg',
			  '../../static/iocn/news-detail2.jpg',
			  '../../static/iocn/news-detail3.jpg',
			  '../../static/iocn/news-detail6.jpg',
			  '../../static/iocn/news-detail5.jpg',
			  
			],
			swiperCurrent: 0,
			
			sortList:[
			  {
			    icon: "../../static/sort/news.png",
			    sortid: 1,
			    text:"最新发布"
			  },{
			    icon: "../../static/sort/second-hand.png",
			    sortid: 2,
			    text:"闲置交易"
			  },{
			    icon: "../../static/sort/love-mood.png",
			    sortid: 3,
			    text:"表白交友"
			  },{
			    icon: "../../static/sort/question-ask.png",
			    sortid: 4,
			    text:"疑问互答"
			  },{
			    icon: "../../static/sort/part-time-job.png",
			    sortid: 5,
			    text:"任务兼职"
			  },{
			    icon: "../../static/sort/study.png",
			    sortid: 6,
			    text:"相约学习"
			  },{
			    icon: "../../static/sort/found.png",
			    sortid: 7,
			    text:"失物招领"
			  },{
			    icon: "../../static/sort/other.png",
			    sortid: 8,
			    text:"趣事分享"
			  },
			],
			testImage:[
			  '../../static/iocn/news-detail1.jpg',
			  '../../static/iocn/news-detail2.jpg',
			  '../../static/iocn/news-detail3.jpg',
			  '../../static/iocn/news-detail5.jpg',
			  '../../static/iocn/news-detail6.jpg',
			  '../../static/iocn/empty.png',
			]
		}
	},
	methods: {
		
	},
	/**
	 * 生命周期函数--监听页面加载
	 */
	onLoad: function (options) {
	  this.setData({
	    navH: app.globalData.navHeight
	  });
	},
	
	//轮播图改变事件
	swiperChange: function (e) {
	  if (e.detail.source === 'touch'){
	      this.swiperCurrent = e.detail.current
	  }
	},
}
</script>

<style>

page {
  background-color: #ffffff;
}


/* 轮播图 */
.bbs-swiper{
  width: 100%;
  height: 100%;
  border-radius: 15rpx;
}

.bbs-swiper-container{
  width: 90%;
  height: 300rpx;
  margin: 0rpx auto;
  position: relative;
  border-radius: 15rpx;
  overflow: hidden;
}

.bbs-swiper-item{
  width: 100%;
  height: 100%;
  border-radius: 20rpx;
}

.bbs-swiper-item>image{
  width: 100%;
  height: 100%;
  border-radius: 15rpx;
}

.bbs-dots{
  width: auto;
  height: 10rpx;
  position: absolute;
  bottom: 20rpx;
  border-radius: 50rpx;
  left: 270rpx;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 3rpx 10rpx;
}
.bbs-dots-item{
  width: 8rpx;
  height: 8rpx;
  margin: 0rpx 8rpx;
  border-radius: 50%;
  background-color: #cdcdcd;
  transition: all .3s;
}
.bbs-dot-active{
  width: 10rpx;
  height: 10rpx;
  background-color: #fff;
}

/* 留言和分类 */
.mess_sort{

  width: 100%;
  background-color: rgb(251, 251, 251);
  /* width: 90%; */
  border-radius: 11%;
  margin: auto;

}


/* 分类标签 */
.sort-nav{
  width: 90%;
  height: 200rpx;
  margin: 0rpx auto;
  /* margin-top: 0rpx; */
  display: flex;
  justify-content: space-between;
  align-items: center;
  align-content: center;
  white-space: nowrap;
  /* padding-bottom: 15rpx; */
  /* padding: 20rpx; */
  /* background-color: rgb(250, 250, 250); */

}

::-webkit-scrollbar {
  
  width: 0;
  height: 0;
  color: transparent;
  display: none;
}
.sort-nav-item{
  display: inline-block;
  width: 94rpx;
  font-size: 20rpx;
  text-align: center;
  /* line-height: 4rpx; */
  color: #aaa;
  margin: 0rpx 34rpx 0rpx 20rpx;
}
.sort-nav-icon{
  width: 84rpx;
  height: 84rpx;
}
.sort-nav-text{
  display: block;
}
.down-selected{
  display: block;
  margin: auto;
  margin-top: 5rpx;
  width: 25rpx;
  height: 25rpx;
}


/* 实时留言 */
.message-image{
  
  width: 60rpx;
  height: 60rpx;
}
.swiper_message{
  float: right;
  display:inline-flex;
  height: 52rpx;
  width: 90%;
}

.swiper-item-message{
  padding: 0;
  display: flex;
}

.message{
  width: 100%;
  height: 52rpx;
  margin: auto 0rpx auto 20rpx;
  align-content: center;
  align-items: center;
  justify-content: flex-start;
  text-overflow: ellipsis;
  
}
.leave-message{
  display: flex;
  width: 85%;
  height: 120rpx;
  margin: auto;
  align-items: center;
  margin-top: 10rpx;
  
  
}

.message-content{
  margin-left: 5px;
  font-size: 25rpx;
  color: #b6b3b3;
}

.message-name{
  padding: 0 4px;
  color: rgb(34, 173, 207);
  font-weight: 400;
  font-size: 27rpx;
  border: rgb(34, 173, 207) 1px solid;
  border-radius: 10rpx;
}


/* 分类具体内容 */
.sort-content{
  
  justify-content: center;
  margin: auto;
  margin-top: 10rpx;
  

}
.sort-content-item{
  
  padding-bottom: 20rpx;
  border-bottom: 5rpx rgb(240, 242, 243) solid ;
}
.user-info{
  width: 88%;
  margin: auto;
  margin-top: 10rpx;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 10rpx;
}

.user-photo{
  display: flex;
  flex-direction: row;
  justify-content: center;
}

.user-info image{
  width: 100rpx;
  border-radius: 50%;
}

.user-detail{
  display: flex;
  flex-direction: column;
  flex-grow: 2;
  justify-content: space-between;
  margin-left: 10rpx;
}

.user-name{
  font-weight: 800;
  color: cadetblue;
}

.user-flag{
  display: flex;
  flex-direction: row;
}

.user-flag view{
  font-weight: 100;
  color: white;
  font-size: 20rpx;
  margin-right: 10rpx;
  padding: 5rpx;
  border-radius: 4rpx;
}

.article-sort{
  background-color: burlywood;
}

.user-sex{
  background-color: chocolate;
}

.user-level{
  background-color: cornflowerblue;
}

.sort-content-middle{
  width: 88%;
  margin: auto;
  padding: 10rpx;
  text-align: center;
}

.acticle-text{
  word-wrap: break-word;
  font-size: 30rpx;
  display: -webkit-box;
  text-align: left;
  overflow: hidden;
  margin-left: 7rpx;
  /* text-align: center; */
  -webkit-line-clamp: 6;
  -webkit-box-orient: vertical;
  letter-spacing: 5rpx;
}

.acticle-image{
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: center;
}

.show-image{
  width: 28vw;
  height: 28vw;
  margin: 7rpx 8rpx 7rpx 2rpx;
}

.show-image image{
  display: inline-block;
  width: 100%;
  height: 100%;
  margin: 5rpx;
  border-radius: 10rpx;
}

/* 更多 */
.post-detail{
  display: block;
  width: 200rpx;
}
.handle{
  padding-left: 170rpx;
}
.handle image{
  
  width: 35rpx;
  height: 35rpx;
  text-align: right;
}
.post-time{
  display: block;
  float: right;
}

.post-time text{
  font-size: 22rpx;
  color: #a09c9c;
}


/* 底部评论等 */
.bottom-img{
  width: 35rpx;
  height: 35rpx;
  vertical-align: middle;
}

.sort-content-bottom{
  height: 52rpx;
  width: 90%;
  display: flex;
  align-content: center;
  margin: auto;
  justify-content: flex-end;
}

.comment{
  margin-left: 20rpx;
  line-height: 52rpx;
}

.like{
  line-height: 52rpx;
}


.num{
  padding-left: 6rpx;
  font-size: 25rpx;
}
</style>
