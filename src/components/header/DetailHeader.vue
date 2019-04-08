<template>
	<div class="detail-header">
		<div class="detail-header-cont">
			<ul class="detail-header-title">
				<li>返回首页</li>
				<li>全部商品</li>
				<li>男装专区</li>
				<li>女装专区</li>
				<li>IP联合系列</li>
				<li>热销专区</li>
				<li>周二上新</li>
				<li>情侣专区</li>
				<li>会员中心</li>
			</ul>
			<div class="logo">
				<img src="../../../static/img/goodsDetail/psd/直播/images/宝贝详情_03.gif"/>
			</div>
			<div class="logo-right">
				<div class="logo-right-top">
					<p><span>￥</span>50</p>
					<p><span>￥</span>20</p>
				</div>
				<ul class="logo-right-mid">
					<li>|</li>
					<li>购物满399可用</li>
					<li>|</li>
					<li>购物满299可用</li>
					<li>|</li>
				</ul>
				<div class="logo-right-bot">
					<p>click</p>
					<p>click</p>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	export default{
		name:'DetailHeader',
		data(){
			return {
				
			}
		}
	}
</script>

<style>
	*{
		list-style: none;
	}
	.detail-header{
		width: 100%;
		height: 150px;
		border-top: 2px solid #E9E4DF;
		border-bottom: 3px solid #92A48E;
	}
	.detail-header-cont{
		width: 1200px;
		height: 150px;
		margin: 0 auto;
	}
	.detail-header-title{
		width: 1000px;
		height: 30px;
		line-height: 30px;
		float: left;
		font-weight: bold;
		display: flex;
		justify-content: space-between;
	}
	.logo{
		width: 1000px;
		float: left;
		margin-top: 20px;
		text-align: center;
	}
	.logo-right{
		width: 200px;
		height: 100px;
		float: left;
	}
	.logo-right-top{
		width: 200px;
		height: 50px;
	}
	.logo-right-top p{
		width: 70px;
		height: 50px;
		text-align: center;
		font-size: 40px;
		font-weight: bold;
		float: left;
		margin-left: 15px;
	}
	.logo-right-top p span{
		font-size: 20px;
		float: left;
		margin-top: 0px;
	}
	.logo-right-mid{
		width: 200px;
		height: 20px;
		line-height: 20px;
		display: flex;
		justify-content: space-between;
	}
	.logo-right-bot{
		display: flex;
		justify-content: space-around;
	}
	.logo-right-bot p{
		width: 60px;
		height: 20px;
		background: black;
		color: white;
		text-align: center;
		line-height: 20px;
	}
</style>