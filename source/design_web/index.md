---
title: design_web
date: 2024-06-29 10:55:40
layout: false
---
{% raw %}
<!DOCTYPE html>
<html lang="zh-CN" data-theme="light">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0,viewport-fit=cover">
        <title>设计网站 | ChuiXue-Lan’s blog</title>
        <meta name="author" content="吹雪">
        <meta name="copyright" content="吹雪">
        <meta name="format-detection" content="telephone=no">
        <meta name="theme-color" content="#ffffff">
        <meta property="og:type" content="website">
        <meta property="og:title" content="设计网站">
        <meta property="og:url" content="https://github.com/ChuiXue-Lan/Blog.git/design_web/index.html">
        <meta property="og:site_name" content="ChuiXue-Lan’s blog">
        <meta property="og:locale" content="zh_CN">
        <meta property="og:image" content="https://github.com/ChuiXue-Lan/Blog.git/img/avatar.jpg">
        <meta property="article:published_time" content="2024-06-27T08:48:16.000Z">
        <meta property="article:modified_time" content="2024-06-30T05:29:43.290Z">
        <meta property="article:author" content="吹雪">
        <meta name="twitter:card" content="summary">
        <meta name="twitter:image" content="https://github.com/ChuiXue-Lan/Blog.git/img/avatar.jpg">
        <link rel="shortcut icon" href="/Blog/img/favicon.png">
        <link rel="canonical" href="https://github.com/ChuiXue-Lan/Blog.git/design_web/index.html">
        <link rel="preconnect" href="//cdn.jsdelivr.net"/>
        <link rel="preconnect" href="//busuanzi.ibruce.info"/>
        <link rel="stylesheet" href="/Blog/css/index.css?v=4.13.0">
        <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.5.1/css/all.min.css">
        <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fancyapps/ui@5.0.33/dist/fancybox/fancybox.min.css" media="print" onload="this.media='all'">
        <script>
            const GLOBAL_CONFIG = {
                root: '/Blog/',
                algolia: undefined,
                localSearch: {
                    "path": "/Blog/search.xml",
                    "preload": false,
                    "top_n_per_article": 1,
                    "unescape": false,
                    "languages": {
                        "hits_empty": "找不到您查询的内容：${query}",
                        "hits_stats": "共找到 ${hits} 篇文章"
                    }
                },
                translate: {
                    "defaultEncoding": 1,
                    "translateDelay": 0,
                    "msgToTraditionalChinese": "繁",
                    "msgToSimplifiedChinese": "简"
                },
                noticeOutdate: undefined,
                highlight: {
                    "plugin": "highlight.js",
                    "highlightCopy": true,
                    "highlightLang": false,
                    "highlightHeightLimit": false
                },
                copy: {
                    success: '复制成功',
                    error: '复制错误',
                    noSupport: '浏览器不支持'
                },
                relativeDate: {
                    homepage: false,
                    post: false
                },
                runtime: '天',
                dateSuffix: {
                    just: '刚刚',
                    min: '分钟前',
                    hour: '小时前',
                    day: '天前',
                    month: '个月前'
                },
                copyright: undefined,
                lightbox: 'fancybox',
                Snackbar: undefined,
                infinitegrid: {
                    js: 'https://cdn.jsdelivr.net/npm/@egjs/infinitegrid@4.11.1/dist/infinitegrid.min.js',
                    buttonText: '加载更多'
                },
                isPhotoFigcaption: false,
                islazyload: false,
                isAnchor: false,
                percent: {
                    toc: true,
                    rightside: true,
                },
                autoDarkmode: false
            }
        </script>
        <script id="config-diff">
            var GLOBAL_CONFIG_SITE = {
                title: '设计网站分享',
                isPost: false,
                isHome: false,
                isHighlightShrink: false,
                isToc: false,
                postUpdate: '2024-06-30 13:29:43'
            }
        </script>
        <link rel="stylesheet" href="APlayer.min.css">
        <div id="aplayer"></div>
        <script src="https://cdn.jsdelivr.net/gh/radium-bit/res@master/live2d/autoload.js" async></script>
        <script>
            (win=>{
                win.saveToLocal = {
                    set: (key,value,ttl)=>{
                        if (ttl === 0)
                            return
                        const now = Date.now()
                        const expiry = now + ttl * 86400000
                        const item = {
                            value,
                            expiry
                        }
                        localStorage.setItem(key, JSON.stringify(item))
                    }
                    ,

                    get: key=>{
                        const itemStr = localStorage.getItem(key)

                        if (!itemStr) {
                            return undefined
                        }
                        const item = JSON.parse(itemStr)
                        const now = Date.now()

                        if (now > item.expiry) {
                            localStorage.removeItem(key)
                            return undefined
                        }
                        return item.value
                    }
                }

                win.getScript = (url,attr={})=>new Promise((resolve,reject)=>{
                    const script = document.createElement('script')
                    script.src = url
                    script.async = true
                    script.onerror = reject
                    script.onload = script.onreadystatechange = function() {
                        const loadState = this.readyState
                        if (loadState && loadState !== 'loaded' && loadState !== 'complete')
                            return
                        script.onload = script.onreadystatechange = null
                        resolve()
                    }

                    Object.keys(attr).forEach(key=>{
                        script.setAttribute(key, attr[key])
                    }
                    )

                    document.head.appendChild(script)
                }
                )

                win.getCSS = (url,id=false)=>new Promise((resolve,reject)=>{
                    const link = document.createElement('link')
                    link.rel = 'stylesheet'
                    link.href = url
                    if (id)
                        link.id = id
                    link.onerror = reject
                    link.onload = link.onreadystatechange = function() {
                        const loadState = this.readyState
                        if (loadState && loadState !== 'loaded' && loadState !== 'complete')
                            return
                        link.onload = link.onreadystatechange = null
                        resolve()
                    }
                    document.head.appendChild(link)
                }
                )

                win.activateDarkMode = ()=>{
                    document.documentElement.setAttribute('data-theme', 'dark')
                    if (document.querySelector('meta[name="theme-color"]') !== null) {
                        document.querySelector('meta[name="theme-color"]').setAttribute('content', '#0d0d0d')
                    }
                }
                win.activateLightMode = ()=>{
                    document.documentElement.setAttribute('data-theme', 'light')
                    if (document.querySelector('meta[name="theme-color"]') !== null) {
                        document.querySelector('meta[name="theme-color"]').setAttribute('content', '#ffffff')
                    }
                }
                const t = saveToLocal.get('theme')

                if (t === 'dark')
                    activateDarkMode()
                else if (t === 'light')
                    activateLightMode()

                const asideStatus = saveToLocal.get('aside-status')
                if (asideStatus !== undefined) {
                    if (asideStatus === 'hide') {
                        document.documentElement.classList.add('hide-aside')
                    } else {
                        document.documentElement.classList.remove('hide-aside')
                    }
                }

                const detectApple = ()=>{
                    if (/iPad|iPhone|iPod|Macintosh/.test(navigator.userAgent)) {
                        document.documentElement.classList.add('apple')
                    }
                }
                detectApple()
            }
            )(window)
        </script>
        <link rel="stylesheet" href="//at.alicdn.com/t/c/font_4603591_gbcr4ig17sl.css">
        <link rel="stylesheet" href="/Blog/css/custom.css">
        <meta name="generator" content="Hexo 7.2.0">
    </head>
    <body>
        <div id="web_bg"></div>
        <div id="sidebar">
            <div id="menu-mask"></div>
            <div id="sidebar-menus">
                <div class="avatar-img is-center">
                    <img src="/Blog/img/avatar.jpg" onerror="onerror=null;src='/img/friend_404.gif'" alt="avatar"/>
                </div>
                <div class="sidebar-site-data site-data is-center">
                    <a href="/Blog/archives/">
                        <div class="headline">文章</div>
                        <div class="length-num">4</div>
                    </a>
                    <a href="/Blog/tags/">
                        <div class="headline">标签</div>
                        <div class="length-num">2</div>
                    </a>
                    <a href="/Blog/categories/">
                        <div class="headline">分类</div>
                        <div class="length-num">2</div>
                    </a>
                </div>
                <hr class="custom-hr"/>
                <div class="menus_items">
                    <div class="menus_item">
                        <a class="site-page" href="/Blog/">
                            <i class="fa-fw fas fa-home"></i>
                            <span>主页</span>
                        </a>
                    </div>
                    <div class="menus_item">
                        <a class="site-page" href="/Blog/konwledge_system/">
                            <i class="fa-fw iconfont icon-tixi"></i>
                            <span>知识体系</span>
                        </a>
                    </div>
                    <div class="menus_item">
                        <a class="site-page group" href="javascript:void(0);">
                            <i class="fa-fw fa fa-graduation-cap"></i>
                            <span>博文</span>
                            <i class="fas fa-chevron-down"></i>
                        </a>
                        <ul class="menus_item_child">
                            <li>
                                <a class="site-page child" href="/Blog/categories/">
                                    <i class="fa-fw fa fa-archive"></i>
                                    <span>分类</span>
                                </a>
                            </li>
                            <li>
                                <a class="site-page child" href="/Blog/tags/">
                                    <i class="fa-fw fa fa-tags"></i>
                                    <span>标签</span>
                                </a>
                            </li>
                            <li>
                                <a class="site-page child" href="/Blog/archives/">
                                    <i class="fa-fw fa fa-folder-open"></i>
                                    <span>归档</span>
                                </a>
                            </li>
                        </ul>
                    </div>
                    <div class="menus_item">
                        <a class="site-page group" href="javascript:void(0);">
                            <i class="fa-fw fas fa-list"></i>
                            <span>分享</span>
                            <i class="fas fa-chevron-down"></i>
                        </a>
                        <ul class="menus_item_child">
                            <li>
                                <a class="site-page child" href="/Blog/music/">
                                    <i class="fa-fw fa fa-music"></i>
                                    <span>音乐</span>
                                </a>
                            </li>
                            <li>
                                <a class="site-page child" href="/Blog/study_source/">
                                    <i class="fa-fw iconfont icon-shu"></i>
                                    <span>学习资源</span>
                                </a>
                            </li>
                            <li>
                                <a class="site-page child" href="/Blog/article/">
                                    <i class="fa-fw iconfont icon-16"></i>
                                    <span>文章分享</span>
                                </a>
                            </li>
                            <li>
                                <a class="site-page child" href="/Blog/design_web/">
                                    <i class="fa-fw iconfont icon-shejishuju"></i>
                                    <span>设计网站</span>
                                </a>·
                            </li>
                        </ul>
                    </div>
                    <div class="menus_item">
                        <a class="site-page" href="/Blog/links/">
                            <i class="fa-fw fa fa-link"></i>
                            <span>友链</span>
                        </a>
                    </div>
                    <div class="menus_item">
                        <a class="site-page" href="/Blog/about/">
                            <i class="fa-fw fas fa-heart"></i>
                            <span>关于笔者</span>
                        </a>
                    </div>
                </div>
            </div>
        </div>
        <div class="page" id="body-wrap">
            <header class="not-home-page" id="page-header" style="background-image: url('/Blog/img/background.jpg')">
                <nav id="nav">
                    <span id="blog-info">
                        <a href="/Blog/" title="ChuiXue-Lan’s blog">
                            <span class="site-name">ChuiXue-Lan’s blog</span>
                        </a>
                    </span>
                    <div id="menus">
                        <div id="search-button">
                            <a class="site-page social-icon search" href="javascript:void(0);">
                                <i class="fas fa-search fa-fw"></i>
                                <span>搜索</span>
                            </a>
                        </div>
                        <div class="menus_items">
                            <div class="menus_item">
                                <a class="site-page" href="/Blog/">
                                    <i class="fa-fw fas fa-home"></i>
                                    <span>主页</span>
                                </a>
                            </div>
                            <div class="menus_item">
                                <a class="site-page" href="/Blog/konwledge_system/">
                                    <i class="fa-fw iconfont icon-tixi"></i>
                                    <span>知识体系</span>
                                </a>
                            </div>
                            <div class="menus_item">
                                <a class="site-page group" href="javascript:void(0);">
                                    <i class="fa-fw fa fa-graduation-cap"></i>
                                    <span>博文</span>
                                    <i class="fas fa-chevron-down"></i>
                                </a>
                                <ul class="menus_item_child">
                                    <li>
                                        <a class="site-page child" href="/Blog/categories/">
                                            <i class="fa-fw fa fa-archive"></i>
                                            <span>分类</span>
                                        </a>
                                    </li>
                                    <li>
                                        <a class="site-page child" href="/Blog/tags/">
                                            <i class="fa-fw fa fa-tags"></i>
                                            <span>标签</span>
                                        </a>
                                    </li>
                                    <li>
                                        <a class="site-page child" href="/Blog/archives/">
                                            <i class="fa-fw fa fa-folder-open"></i>
                                            <span>归档</span>
                                        </a>
                                    </li>
                                </ul>
                            </div>
                            <div class="menus_item">
                                <a class="site-page group" href="javascript:void(0);">
                                    <i class="fa-fw fas fa-list"></i>
                                    <span>分享</span>
                                    <i class="fas fa-chevron-down"></i>
                                </a>
                                <ul class="menus_item_child">
                                    <li>
                                        <a class="site-page child" href="/Blog/music/">
                                            <i class="fa-fw fa fa-music"></i>
                                            <span>音乐</span>
                                        </a>
                                    </li>
                                    <li>
                                        <a class="site-page child" href="/Blog/study_source/">
                                            <i class="fa-fw iconfont icon-shu"></i>
                                            <span>学习资源</span>
                                        </a>
                                    </li>
                                    <li>
                                        <a class="site-page child" href="/Blog/article/">
                                            <i class="fa-fw iconfont icon-16"></i>
                                            <span>文章分享</span>
                                        </a>
                                    </li>
                                    <li>
                                        <a class="site-page child" href="/Blog/design_web/">
                                            <i class="fa-fw iconfont icon-shejishuju"></i>
                                            <span>设计网站</span>
                                        </a>
                                    </li>
                                </ul>
                            </div>
                            <div class="menus_item">
                                <a class="site-page" href="/Blog/links/">
                                    <i class="fa-fw fa fa-link"></i>
                                    <span>友链</span>
                                </a>
                            </div>
                            <div class="menus_item">
                                <a class="site-page" href="/Blog/about/">
                                    <i class="fa-fw fas fa-heart"></i>
                                    <span>关于笔者</span>
                                </a>
                            </div>
                        </div>
                        <div id="toggle-menu">
                            <a class="site-page" href="javascript:void(0);">
                                <i class="fas fa-bars fa-fw"></i>
                            </a>
                        </div>
                    </div>
                </nav>
                <div id="page-site-info">
                    <h1 id="site-title">设计网站分享</h1>
                </div>
            </header>
            <main class="layout" id="content-inner">
                <div id="page">
                    <div id="article-container">
                        <div class="flink">
                            <script>
                                (()=>{
                                    const replaceSymbol = (str)=>{
                                        return str.replace(/[\p{P}\p{S}]/gu, "-")
                                    }

                                    let result = ""
                                    const add = (str)=>{
                                        for (let i = 0; i < str.length; i++) {
                                            const replaceClassName = replaceSymbol(str[i].class_name)
                                            const className = str[i].class_name ? `<h2 id="${replaceClassName}"><a href="#${replaceClassName}" class="headerlink" title="${str[i].class_name}"></a>${str[i].class_name}</h2>` : ""
                                            const classDesc = str[i].class_desc ? `<div class="flink-desc">${str[i].class_desc}</div>` : ""

                                            let listResult = ""
                                            const lists = str[i].link_list
                                            if (true) {
                                                lists.sort(()=>Math.random() - 0.5)
                                            }
                                            for (let j = 0; j < lists.length; j++) {
                                                listResult += `
          <div class="flink-list-item">
            <a href="${lists[j].link}" title="${lists[j].name}" target="_blank">
              <div class="flink-item-icon">
                <img class="no-lightbox" src="${lists[j].avatar}" onerror='this.onerror=null;this.src="/Blog/img/friend_404.gif"' alt="${lists[j].name}" />
              </div>
              <div class="flink-item-name">${lists[j].name}</div> 
              <div class="flink-item-desc" title="${lists[j].descr}">${lists[j].descr}</div>
            </a>
          </div>`
                                            }

                                            result += `${className}${classDesc} <div class="flink-list">${listResult}</div>`
                                        }

                                        document.querySelector(".flink").insertAdjacentHTML("afterbegin", result)
                                        window.lazyLoadInstance && window.lazyLoadInstance.update()
                                    }

                                    const linkData = [{
                                        "class_name": "图标类",
                                        "class_desc": "在设计过程用到的图标网站",
                                        "link_list": [{
                                            "name": "iconfont",
                                            "link": "https://www.iconfont.cn/",
                                            "avatar": "/Blog/img/default_cover.jpg",
                                            "descr": "阿里巴巴矢量图标库"
                                        }, {
                                            "name": "hatchful",
                                            "link": "https://www.shopify.com/zh/tools/logo-maker",
                                            "avatar": "/Blog/img/default_cover.jpg",
                                            "descr": "免费的logo制作器"
                                        }]
                                    }, {
                                        "class_name": "样式类",
                                        "class_desc": "值得推荐的前端样式网站",
                                        "link_list": [{
                                            "name": "渐变颜色",
                                            "link": "https://color.oulu.me/",
                                            "avatar": "/Blog/img/default_cover.jpg",
                                            "descr": "一个集合180种免费的线性渐变网站，可在任何网站使用"
                                        }]
                                    }, {
                                        "class_name": "图片类",
                                        "class_desc": "很赞的4K图片",
                                        "link_list": [{
                                            "name": "彼岸图库",
                                            "link": "https://pic.netbian.com/4kfengjing/index_2.html",
                                            "avatar": "/Blog/img/default_cover.jpg",
                                            "descr": "每天一张免费背景",
                                        }]
                                    }]
                                    if (false) {
                                        fetch("/Blog/").then(response=>response.json()).then(add)
                                    } else if (linkData) {
                                        add(linkData)
                                    }
                                }
                                )()
                            </script>
                        </div>
                    </div>
                    <hr class="custom-hr"/>
                    <div id="post-comment">
                        <div class="comment-head">
                            <div class="comment-headline">
                                <i class="fas fa-comments fa-fw"></i>
                                <span>评论</span>
                            </div>
                            <div class="comment-switch">
                                <span class="first-comment">Twikoo</span>
                                <span id="switch-btn"></span>
                                <span class="second-comment">Valine</span>
                            </div>
                        </div>
                        <div class="comment-wrap">
                            <div>
                                <div id="twikoo-wrap"></div>
                            </div>
                            <div>
                                <div class="vcomment" id="vcomment"></div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="aside-content" id="aside-content">
                    <div class="card-widget card-info">
                        <div class="is-center">
                            <div class="avatar-img">
                                <img src="/Blog/img/avatar.jpg" onerror="this.onerror=null;this.src='/Blog/img/friend_404.gif'" alt="avatar"/>
                            </div>
                            <div class="author-info__name">吹雪</div>
                            <div class="author-info__description">心中有火，逆流而上</div>
                        </div>
                        <div class="card-info-data site-data is-center">
                            <a href="/Blog/archives/">
                                <div class="headline">文章</div>
                                <div class="length-num">4</div>
                            </a>
                            <a href="/Blog/tags/">
                                <div class="headline">标签</div>
                                <div class="length-num">2</div>
                            </a>
                            <a href="/Blog/categories/">
                                <div class="headline">分类</div>
                                <div class="length-num">2</div>
                            </a>
                        </div>
                        <a id="card-info-btn" href="https://github.com/ChuiXue-Lan">
                            <i class="fab fa-github"></i>
                            <span>Follow Me</span>
                        </a>
                        <div class="card-info-social-icons is-center">
                            <a class="social-icon" href="https://github.com/ChuiXue-Lan" target="_blank" title="Github">
                                <i class="fab fa-github"></i>
                            </a>
                            <a class="social-icon" href="mailto:2358369326@qq.com" target="_blank" title="Email">
                                <i class="fas fa-envelope-open-text"></i>
                            </a>
                        </div>
                    </div>
                    <div class="card-widget card-announcement">
                        <div class="item-headline">
                            <i class="fas fa-bullhorn fa-shake"></i>
                            <span>公告</span>
                        </div>
                        <div class="announcement_content">
                            欢迎光临小站，这里是我日常工作和学习中收集、整理和编写的文章<br />本站的内容经过个人加工总结而来，也参考了网友们分享的资料，如有侵权请联系我及时进行修改或删除😊
                        </div>
                    </div>
                    <div class="sticky_layout">
                        <div class="card-widget card-recent-post">
                            <div class="item-headline">
                                <i class="fas fa-history"></i>
                                <span>最新文章</span>
                            </div>
                            <div class="aside-list">
                                <div class="aside-list-item no-cover">
                                    <div class="content">
                                        <a class="title" href="/Blog/2024/06/30/%E7%9B%AE%E5%BD%95/" title="本站的阅读指南">本站的阅读指南</a>
                                        <time datetime="2024-06-29T20:53:54.000Z" title="发表于 2024-06-30 04:53:54">2024-06-30</time>
                                    </div>
                                </div>
                                <div class="aside-list-item">
                                    <a class="thumbnail" href="/Blog/2024/06/28/YOLOv8-%E4%BD%BF%E7%94%A8%E6%9C%8D%E5%8A%A1%E5%99%A8%E8%AE%AD%E7%BB%83%E6%A8%A1%E5%9E%8B/" title="YOLOv8-使用服务器训练模型">
                                        <img src="/Blog/img/cover1.jpg" onerror="this.onerror=null;this.src='/Blog/img/404.jpg'" alt="YOLOv8-使用服务器训练模型"/>
                                    </a>
                                    <div class="content">
                                        <a class="title" href="/Blog/2024/06/28/YOLOv8-%E4%BD%BF%E7%94%A8%E6%9C%8D%E5%8A%A1%E5%99%A8%E8%AE%AD%E7%BB%83%E6%A8%A1%E5%9E%8B/" title="YOLOv8-使用服务器训练模型">YOLOv8-使用服务器训练模型</a>
                                        <time datetime="2024-06-27T23:14:17.000Z" title="发表于 2024-06-28 07:14:17">2024-06-28</time>
                                    </div>
                                </div>
                                <div class="aside-list-item">
                                    <a class="thumbnail" href="/Blog/2024/06/28/YOLOv8-%E8%87%AA%E5%AE%9A%E4%B9%89%E6%95%B0%E6%8D%AE%E9%9B%86%E5%B9%B6%E8%AE%AD%E7%BB%83/" title="YOLOv8 - 自定义数据集并训练">
                                        <img src="/Blog/img/cover1.jpg" onerror="this.onerror=null;this.src='/Blog/img/404.jpg'" alt="YOLOv8 - 自定义数据集并训练"/>
                                    </a>
                                    <div class="content">
                                        <a class="title" href="/Blog/2024/06/28/YOLOv8-%E8%87%AA%E5%AE%9A%E4%B9%89%E6%95%B0%E6%8D%AE%E9%9B%86%E5%B9%B6%E8%AE%AD%E7%BB%83/" title="YOLOv8 - 自定义数据集并训练">YOLOv8 - 自定义数据集并训练</a>
                                        <time datetime="2024-06-27T22:25:06.000Z" title="发表于 2024-06-28 06:25:06">2024-06-28</time>
                                    </div>
                                </div>
                                <div class="aside-list-item">
                                    <a class="thumbnail" href="/Blog/2024/06/28/YOLOv8-%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/" title="YOLOv8 - 环境配置">
                                        <img src="/Blog/img/background2.jpg" onerror="this.onerror=null;this.src='/Blog/img/404.jpg'" alt="YOLOv8 - 环境配置"/>
                                    </a>
                                    <div class="content">
                                        <a class="title" href="/Blog/2024/06/28/YOLOv8-%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/" title="YOLOv8 - 环境配置">YOLOv8 - 环境配置</a>
                                        <time datetime="2024-06-27T21:25:53.000Z" title="发表于 2024-06-28 05:25:53">2024-06-28</time>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="card-widget card-categories">
                            <div class="item-headline">
                                <i class="fas fa-folder-open"></i>
                                <span>分类</span>
                            </div>
                            <ul class="card-category-list" id="aside-cat-list">
                                <li class="card-category-list-item ">
                                    <a class="card-category-list-link" href="/Blog/categories/Computer-Vision/">
                                        <span class="card-category-list-name">Computer Vision</span>
                                        <span class="card-category-list-count">3</span>
                                    </a>
                                </li>
                                <li class="card-category-list-item ">
                                    <a class="card-category-list-link" href="/Blog/categories/%E5%85%B6%E4%BB%96/">
                                        <span class="card-category-list-name">其他</span>
                                        <span class="card-category-list-count">1</span>
                                    </a>
                                </li>
                            </ul>
                        </div>
                        <div class="card-widget card-tags">
                            <div class="item-headline">
                                <i class="fas fa-tags"></i>
                                <span>标签</span>
                            </div>
                            <div class="card-tag-cloud">
                                <a href="/Blog/tags/YOLOv8/" style="font-size: 1.5em; color: #99a9bf">YOLOv8</a>
                                <a href="/Blog/tags/%E9%98%85%E8%AF%BB%E6%8C%87%E5%8D%97/" style="font-size: 1.1em; color: #999">阅读指南</a>
                            </div>
                        </div>
                        <div class="card-widget card-archives">
                            <div class="item-headline">
                                <i class="fas fa-archive"></i>
                                <span>归档</span>
                            </div>
                            <ul class="card-archive-list">
                                <li class="card-archive-list-item">
                                    <a class="card-archive-list-link" href="/Blog/archives/2024/06/">
                                        <span class="card-archive-list-date">六月 2024</span>
                                        <span class="card-archive-list-count">4</span>
                                    </a>
                                </li>
                            </ul>
                        </div>
                        <div class="card-widget card-webinfo">
                            <div class="item-headline">
                                <i class="fas fa-chart-line"></i>
                                <span>网站资讯</span>
                            </div>
                            <div class="webinfo">
                                <div class="webinfo-item">
                                    <div class="item-name">文章数目 :</div>
                                    <div class="item-count">4</div>
                                </div>
                                <div class="webinfo-item">
                                    <div class="item-name">已运行时间 :</div>
                                    <div class="item-count" id="runtimeshow" data-publishDate="2024-06-25T16:00:00.000Z">
                                        <i class="fa-solid fa-spinner fa-spin"></i>
                                    </div>
                                </div>
                                <div class="webinfo-item">
                                    <div class="item-name">本站总字数 :</div>
                                    <div class="item-count">3.9k</div>
                                </div>
                                <div class="webinfo-item">
                                    <div class="item-name">本站访客数 :</div>
                                    <div class="item-count" id="busuanzi_value_site_uv">
                                        <i class="fa-solid fa-spinner fa-spin"></i>
                                    </div>
                                </div>
                                <div class="webinfo-item">
                                    <div class="item-name">本站总访问量 :</div>
                                    <div class="item-count" id="busuanzi_value_site_pv">
                                        <i class="fa-solid fa-spinner fa-spin"></i>
                                    </div>
                                </div>
                                <div class="webinfo-item">
                                    <div class="item-name">最后更新时间 :</div>
                                    <div class="item-count" id="last-push-date" data-lastPushDate="2024-06-30T08:38:36.663Z">
                                        <i class="fa-solid fa-spinner fa-spin"></i>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </main>
            <footer id="footer" style="background-image: url('/Blog/img/background.jpg')">
                <div id="footer-wrap">
                    <div class="copyright">&copy;2024 By 吹雪</div>
                    <div class="framework-info">
                        <span>框架 </span>
                        <a target="_blank" rel="noopener" href="https://hexo.io">Hexo</a>
                        <span class="footer-separator">|</span>
                        <span>主题 </span>
                        <a href="https://github.com/jerryc127/hexo-theme-butterfly">Butterfly</a>
                    </div>
                    <div class="footer_custom_text">人民有信仰 国家有力量 民族有希望</div>
                </div>
            </footer>
        </div>
        <div id="rightside">
            <div id="rightside-config-hide">
                <button id="translateLink" type="button" title="简繁转换">简</button>
                <button id="darkmode" type="button" title="浅色和深色模式转换">
                    <i class="fas fa-adjust"></i>
                </button>
                <button id="hide-aside-btn" type="button" title="单栏和双栏切换">
                    <i class="fas fa-arrows-alt-h"></i>
                </button>
            </div>
            <div id="rightside-config-show">
                <button id="rightside-config" type="button" title="设置">
                    <i class="fas fa-cog fa-spin"></i>
                </button>
                <a id="to_comment" href="#post-comment" title="直达评论">
                    <i class="fas fa-comments"></i>
                </a>
                <button id="go-up" type="button" title="回到顶部">
                    <span class="scroll-percent"></span>
                    <i class="fas fa-arrow-up"></i>
                </button>
            </div>
        </div>
        <div>
            <script src="/Blog/js/utils.js?v=4.13.0"></script>
            <script src="/Blog/js/main.js?v=4.13.0"></script>
            <script src="/Blog/js/tw_cn.js?v=4.13.0"></script>
            <script src="https://cdn.jsdelivr.net/npm/@fancyapps/ui@5.0.33/dist/fancybox/fancybox.umd.min.js"></script>
            <div class="js-pjax">
                <script>
                    (()=>{
                        const getCount = ()=>{
                            const countELement = document.getElementById('twikoo-count')
                            if (!countELement)
                                return
                            twikoo.getCommentsCount({
                                envId: '',
                                region: '',
                                urls: [window.location.pathname],
                                includeReply: false
                            }).then(res=>{
                                countELement.textContent = res[0].count
                            }
                            ).catch(err=>{
                                console.error(err)
                            }
                            )
                        }

                        const init = ()=>{
                            twikoo.init(Object.assign({
                                el: '#twikoo-wrap',
                                envId: '',
                                region: '',
                                onCommentLoaded: ()=>{
                                    btf.loadLightbox(document.querySelectorAll('#twikoo .tk-content img:not(.tk-owo-emotion)'))
                                }
                            }, null))

                            GLOBAL_CONFIG_SITE.isPost && getCount()
                        }

                        const loadTwikoo = ()=>{
                            if (typeof twikoo === 'object')
                                setTimeout(init, 0)
                            else
                                getScript('https://cdn.jsdelivr.net/npm/twikoo@1.6.31/dist/twikoo.all.min.js').then(init)
                        }

                        if ('Twikoo' === 'Twikoo' || !true) {
                            if (true)
                                btf.loadComment(document.getElementById('twikoo-wrap'), loadTwikoo)
                            else
                                loadTwikoo()
                        } else {
                            window.loadOtherComment = loadTwikoo
                        }
                    }
                    )()
                </script>
                <script>
                    (()=>{
                        const initValine = ()=>{
                            const valine = new Valine(Object.assign({
                                el: '#vcomment',
                                appId: '',
                                appKey: '',
                                avatar: 'monsterid',
                                serverURLs: '',
                                emojiMaps: "",
                                path: window.location.pathname,
                                visitor: false
                            }, null))
                        }

                        const loadValine = async()=>{
                            if (typeof Valine === 'function')
                                initValine()
                            else {
                                await getScript('https://cdn.jsdelivr.net/npm/valine@1.5.1/dist/Valine.min.js')
                                initValine()
                            }
                        }

                        if ('Twikoo' === 'Valine' || !true) {
                            if (true)
                                btf.loadComment(document.getElementById('vcomment'), loadValine)
                            else
                                setTimeout(loadValine, 0)
                        } else {
                            window.loadOtherComment = loadValine
                        }
                    }
                    )()
                </script>
            </div>
            <script defer="defer" id="fluttering_ribbon" mobile="true" src="https://cdn.jsdelivr.net/npm/butterfly-extsrc@1.1.3/dist/canvas-fluttering-ribbon.min.js"></script>
            <script async data-pjax src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>
            <div id="local-search">
                <div class="search-dialog">
                    <nav class="search-nav">
                        <span class="search-dialog-title">搜索</span>
                        <span id="loading-status"></span>
                        <button class="search-close-button">
                            <i class="fas fa-times"></i>
                        </button>
                    </nav>
                    <div class="is-center" id="loading-database">
                        <i class="fas fa-spinner fa-pulse"></i>
                        <span>数据库加载中</span>
                    </div>
                    <div class="search-wrap">
                        <div id="local-search-input">
                            <div class="local-search-box">
                                <input class="local-search-box--input" placeholder="搜索文章" type="text"/>
                            </div>
                        </div>
                        <hr/>
                        <div id="local-search-results"></div>
                        <div id="local-search-stats-wrap"></div>
                    </div>
                </div>
                <div id="search-mask"></div>
                <script src="/Blog/js/search/local-search.js?v=4.13.0"></script>
            </div>
        </div>
    </body>
</html>

{% endraw %}