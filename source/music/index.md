---
# title：音乐页面显示的标题
title: 音乐
# date：音乐页面的创建日期和时间
date: 2026-09-01 17:20:00
# description：搜索结果和社交分享中使用的页面摘要，避免把播放器代码当成摘要
description: 使用 APlayer 播放博客中的本地音频，并记录静态音乐播放器的配置方法。
# comments：当前没有配置评论服务，因此关闭此页面的评论区域
comments: false
# aside：音乐播放器需要较宽的展示区域，因此只在此页面隐藏右侧栏
aside: false
---

# 我的音乐

这里用于播放博客中的音频内容。当前曲目是一段本地测试旋律，用于验证播放器、静态音频文件和 GitHub Pages 的完整加载链路。

<!-- APlayer 的样式和脚本只在音乐页面加载，避免其他页面增加不必要的网络请求。 -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/aplayer@1.10.1/dist/APlayer.min.css">

<div id="music-player"></div>

<script src="https://cdn.jsdelivr.net/npm/aplayer@1.10.1/dist/APlayer.min.js"></script>
<script>
  // 使用项目内的本地音频，不依赖需要登录或可能失效的第三方歌单接口。
  const musicPlayer = new APlayer({
    container: document.getElementById('music-player'),
    autoplay: false,
    mutex: true,
    loop: 'all',
    order: 'list',
    preload: 'metadata',
    volume: 0.5,
    audio: [
      {
        name: '博客测试旋律',
        artist: 'Laor 的博客',
        url: '/personal-blog/audio/demo-melody.wav',
        cover: '/personal-blog/img/头像.jpg',
        theme: '#49b1f5',
        type: 'auto'
      }
    ]
  })
</script>

> 浏览器不会自动播放音乐。请主动点击播放按钮，避免打开网站时突然发出声音。
