---
title: 友圈鱼塘
aside: false
comment: false
---

# 友圈鱼塘

<div class="friend-circle-container">
  <div class="root-container">
      <div id="friend-circle-lite-root"></div>
  </div>
</div>

<style>
.friend-circle-container {
    font-family: Arial, sans-serif;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    margin: 0;
    overflow-y: scroll;
    overflow-x: hidden;
}
.root-container {
    width: 100%;
    margin-top: 40px;
    max-width: 1100px;
}
@media (max-width: 1200px) {
    .root-container {
        max-width: 95%;
        margin-top: 20px;
    }
}
</style>

<script setup>
import { onMounted } from 'vue'

onMounted(() => {
    // 设置 UserConfig 配置，避免页面加载时未定义
    if (typeof window.UserConfig === 'undefined') {
        window.UserConfig = {
            private_api_url: 'https://friend.xingji.fun/',
            page_turning_number: 20,
            error_img: 'https://cdn.bsgun.cn/Hexo-static/img/error-404.avif'
        }
    }

    // 动态加载 fclite.js 并确保初始化
    const script = document.createElement('script');
    script.src = "/js/fclite.js";
    script.defer = true;
    script.onload = () => {
        // 确保 fclite.js 初始化完成
        if (typeof window.FriendCircleLite !== 'undefined') {
            window.FriendCircleLite.init();
        }
    };
    document.body.appendChild(script);
})
</script>

<link rel="stylesheet" href="/css/fclite.css">
