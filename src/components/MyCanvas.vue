<template>
  <canvas id="mycanvas" ref="canvas"></canvas>
</template>

<script>
export default {
  methods: {
    drawCurrentTime() {
      const canvas = this.$refs.canvas;
      const ctx = canvas.getContext('2d');
      
      // 设置 canvas 大小
      canvas.width = 210;
      canvas.height = 210;

      // 获取当前时间
      const currentTime = new Date();
      const formattedTime = `${currentTime.getFullYear()}-${String(currentTime.getMonth() + 1).padStart(2, '0')}-${String(currentTime.getDate()).padStart(2, '0')} ${String(currentTime.getHours()).padStart(2, '0')}:${String(currentTime.getMinutes()).padStart(2, '0')}:${String(currentTime.getSeconds()).padStart(2, '0')}`;
      const carliscense = `赣ALJ6091`;
      const text = carliscense + `#` + formattedTime;
      const lines = text.split('#');

      // 清空 canvas
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      // 绘制文字
      ctx.rotate(-20*Math.PI/180);
      ctx.font = '18px Vedana';
      ctx.fillStyle = "rgba(30, 143, 105, 0.43)"; // 设置文字颜色
      const x = 21.1;
      const y = 30.7;
      for (let i = 0; i < lines.length; i++) {
          ctx.fillText(lines[i], x, y + 26 * (i + 1));
        }

      // 获取图片地址 (image/png)
      const imageUrl = canvas.toDataURL('image/png');

      // 将图片地址通过事件传递给父组件
      this.$emit('canvas-updated', imageUrl);
    }
  },
  mounted() {
    this.drawCurrentTime();
  }
};
</script>

<style>
canvas {
  display: none;
}
</style>
