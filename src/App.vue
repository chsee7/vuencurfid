<template>
  <div id="app">
    <app1 :backgroundImage="canvasImageUrl" />
     <div data-v-app="" style="z-index: 0; background-color: rgba(255, 255, 255, 0); position: fixed; width: 100%;"><div data-v-a4b10d5c="" class="contentBox">
				<div data-v-a4b10d5c="" class="card-box">
					<div data-v-a4b10d5c="" class="card-line">
						<div data-v-a4b10d5c="" class="label">车牌号</div>
						<div data-v-a4b10d5c="" class="value">赣ALJ6091</div>
					</div>
					<div data-v-a4b10d5c="" class="card-line">
						<div data-v-a4b10d5c="" class="label">车主姓名</div>
						<div data-v-a4b10d5c="" class="value">陈**</div>
					</div>
					<div data-v-a4b10d5c="" class="card-line">
						<div data-v-a4b10d5c="" class="label">入网时间</div>
						<div data-v-a4b10d5c="" class="value">2023-10-31 10:35:07</div>
					</div>
					<div data-v-a4b10d5c="" class="card-line">
						<div data-v-a4b10d5c="" class="label">防伪图片</div>
						<div data-v-a4b10d5c="" class="value">
							<div data-v-a4b10d5c="" class="el-image">
								<img id="img1" src="photo.png" @click="showOverlay" style="width:100%; height:100%; position:relative; display:inline-block; overflow:hidden; vertical-align:top; opacity:1;">
								
								<div v-if="isOverlayVisible" id="overlay" class="el-image-viewer__wrapper" tabindex="-1" style="z-index: 888;">
									<div class="el-image-viewer__mask"></div>
									<span class="el-image-viewer__btn el-image-viewer__close" style="border-radius:50%;background-color:#606266">
										<i @click="closeOverlay" class="el-icon">
											<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1024 1024">
												<path fill="currentColor" d="M764.288 214.592 512 466.88 259.712 214.592a31.936 31.936 0 0 0-45.12 45.12L466.752 512 214.528 764.224a31.936 31.936 0 1 0 45.12 45.184L512 557.184l252.288 252.288a31.936 31.936 0 0 0 45.12-45.12L557.12 512.064l252.288-252.352a31.936 31.936 0 1 0-45.12-45.184z">
												</path>
											</svg>
										</i>
									</span>
									<div class="el-image-viewer__btn el-image-viewer__actions">
										<div id="toolbar" class="el-image-viewer__actions__inner">					
											<i @click="zoomOut" class="el-icon">
												<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1024 1024">
													<path fill="currentColor" d="m795.904 750.72 124.992 124.928a32 32 0 0 1-45.248 45.248L750.656 795.904a416 416 0 1 1 45.248-45.248zM480 832a352 352 0 1 0 0-704 352 352 0 0 0 0 704zM352 448h256a32 32 0 0 1 0 64H352a32 32 0 0 1 0-64z"></path>
												</svg>
											</i>
											<i @click="zoomIn" class="el-icon">
												<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1024 1024">
													<path fill="currentColor" d="m795.904 750.72 124.992 124.928a32 32 0 0 1-45.248 45.248L750.656 795.904a416 416 0 1 1 45.248-45.248zM480 832a352 352 0 1 0 0-704 352 352 0 0 0 0 704zm-32-384v-96a32 32 0 0 1 64 0v96h96a32 32 0 0 1 0 64h-96v96a32 32 0 0 1-64 0v-96h-96a32 32 0 0 1 0-64h96z"></path>
												</svg>
											</i>
											<i class="el-image-viewer__actions__divider"></i>
											<i @click="resetImage" class="el-icon">
												<svg @click="toggleSvg" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1024 1024">
													<path :d="currentPath" fill="currentColor"></path>
												</svg>
											</i>
											<i class="el-image-viewer__actions__divider"></i>
											<i @click="rotateLeft" class="el-icon">
												<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1024 1024">
													<path fill="currentColor" d="M289.088 296.704h92.992a32 32 0 0 1 0 64H232.96a32 32 0 0 1-32-32V179.712a32 32 0 0 1 64 0v50.56a384 384 0 0 1 643.84 282.88 384 384 0 0 1-383.936 384 384 384 0 0 1-384-384h64a320 320 0 1 0 640 0 320 320 0 0 0-555.712-216.448z"></path>
												</svg>
											</i>
											<i @click="rotateRight" class="el-icon">
												<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1024 1024">
													<path fill="currentColor" d="M784.512 230.272v-50.56a32 32 0 1 1 64 0v149.056a32 32 0 0 1-32 32H667.52a32 32 0 1 1 0-64h92.992A320 320 0 1 0 524.8 833.152a320 320 0 0 0 320-320h64a384 384 0 0 1-384 384 384 384 0 0 1-384-384 384 384 0 0 1 643.712-282.88z"></path>
												</svg>
											</i>					
										</div>
									</div>
									<div class="el-image-viewer__canvas">
										<img :src="imageSrc" :style="{ transform: `scale(${scale}) rotate(${rotation}deg)` }" ref="image" alt="image" />
									</div>
								</div>
								
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
    <my-canvas @canvas-updated="updateCanvasImage" />
  </div>
</template>

<script>
import MyCanvas from './components/MyCanvas.vue';
import App1 from './components/App1.vue';

export default {
  components: {
    MyCanvas,
    App1
  },
  data() {
    return {
      canvasImageUrl: '', // 用于保存从 canvas 生成的图片 URL
      isOverlayVisible: false,   // 控制浮层显示
      scale: 1, // 图片缩放比例
      rotation: 0,               // 旋转角度
      imageSrc: "", // 图片来源
      // 原始路径内容
      originalPath: "m160 96.064 192 .192a32 32 0 0 1 0 64l-192-.192V352a32 32 0 0 1-64 0V96h64v.064zm0 831.872V928H96V672a32 32 0 1 1 64 0v191.936l192-.192a32 32 0 1 1 0 64l-192 .192zM864 96.064V96h64v256a32 32 0 1 1-64 0V160.064l-192 .192a32 32 0 1 1 0-64l192-.192zm0 831.872-192-.192a32 32 0 0 1 0-64l192 .192V672a32 32 0 1 1 64 0v256h-64v-.064z",
      
      // 切换后的路径内容
      newPath: "M813.176 180.706a60.235 60.235 0 0 1 60.236 60.235v481.883a60.235 60.235 0 0 1-60.236 60.235H210.824a60.235 60.235 0 0 1-60.236-60.235V240.94a60.235 60.235 0 0 1 60.236-60.235h602.352zm0-60.235H210.824A120.47 120.47 0 0 0 90.353 240.94v481.883a120.47 120.47 0 0 0 120.47 120.47h602.353a120.47 120.47 0 0 0 120.471-120.47V240.94a120.47 120.47 0 0 0-120.47-120.47zm-120.47 180.705a30.118 30.118 0 0 0-30.118 30.118v301.177a30.118 30.118 0 0 0 60.236 0V331.294a30.118 30.118 0 0 0-30.118-30.118zm-361.412 0a30.118 30.118 0 0 0-30.118 30.118v301.177a30.118 30.118 0 1 0 60.236 0V331.294a30.118 30.118 0 0 0-30.118-30.118zM512 361.412a30.118 30.118 0 0 0-30.118 30.117v30.118a30.118 30.118 0 0 0 60.236 0V391.53A30.118 30.118 0 0 0 512 361.412zM512 512a30.118 30.118 0 0 0-30.118 30.118v30.117a30.118 30.118 0 0 0 60.236 0v-30.117A30.118 30.118 0 0 0 512 512z",

      // 当前路径
      currentPath: "",
    };
  },
  created() {
    // 初始化为原始路径
    this.currentPath = this.originalPath;
  },
  methods: {
    // 更新 canvasImageUrl 的方法
    updateCanvasImage(imageUrl) {
      this.canvasImageUrl = imageUrl;
    },
    // 打开浮层并设置图片源
    showOverlay() {
      const imgElement = document.getElementById('img1');
      this.imageSrc = imgElement.src;
      this.isOverlayVisible = true;
    },
    // 关闭浮层
    closeOverlay() {
      this.isOverlayVisible = false;
      this.resetImage(); // 关闭时重置图片状态
    },
    // 放大图片
    zoomIn() {
      this.scale *= 1.2; // 每次放大1.2倍
    },
    // 缩小图片
    zoomOut() {
      this.scale *= 0.8333; // 每次缩小为原来的5/6倍
    },
    // 复原图片
    resetImage() {
      this.scale = 1;
      this.rotation = 0;
    },
    // 向左旋转
    rotateLeft() {
      this.rotation -= 90;
    },
    // 向右旋转
    rotateRight() {
      this.rotation += 90;
    },
    // 切换 SVG 的路径内容
    toggleSvg() {
      // 切换路径，当前路径和新路径不同则切换到新路径，反之则恢复原始路径
      this.currentPath = this.currentPath === this.originalPath ? this.newPath : this.originalPath;
    },
  },
};
</script>

<style>
#app {
  top: 0px;
  left: 0px;
  position: relative;
  width: 100%;
}

.overlay-content img {
  max-width: 100%;   /* 设置最大宽度为100% */
  max-height: 100%;  /* 设置最大高度为100% */
  transition: transform 0.3s ease;
}

.el-image-viewer__wrapper{position:fixed;top:0;left:0;right:0;bottom:0;width:100%;}

.el-image-viewer__btn{position:absolute;z-index:1;display:flex;align-items:center;justify-content:center;border-radius:50%;opacity:.8;cursor:pointer;box-sizing:border-box;-webkit-user-select:none;user-select:none}

.el-image-viewer__btn .el-icon{font-size:inherit;cursor:pointer}

.el-image-viewer__close{top:40px;right:40px;width:40px;height:40px;font-size:40px}

.el-image-viewer__canvas{position:static;width:100%;height:100%;display:flex;justify-content:center;align-items:center;-webkit-user-select:none;user-select:none}

.el-image-viewer__actions{left:50%;bottom:30px;transform:translate(-50%);width:282px;height:44px;padding:0 23px;background-color:#606266;border-color:#fff;border-radius:22px}

.el-image-viewer__actions__inner{width:100%;height:100%;text-align:justify;cursor:default;font-size:23px;color:#fff;display:flex;align-items:center;justify-content:space-around}

.el-image-viewer__prev{top:50%;transform:translateY(-50%);left:40px;width:44px;height:44px;font-size:24px;color:#fff;background-color:#606266;border-color:#fff}

.el-image-viewer__next{top:50%;transform:translateY(-50%);right:40px;text-indent:2px;width:44px;height:44px;font-size:24px;color:#fff;background-color:#606266;border-color:#fff}

.el-image-viewer__close{width:44px;height:44px;font-size:24px;color:#fff;background-color:var(--el-text-color-regular);border-color:#fff}

.el-image-viewer__mask{position:absolute;width:100%;height:100%;top:0;left:0;opacity:.5;background:#000}
</style>