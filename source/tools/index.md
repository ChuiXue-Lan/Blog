---
title: 工具/学习网站
date: 2024-06-30 17:29:14
---
{% raw %}
<div class="flink">
  <script>
    (() => {
      const replaceSymbol = (str) => {
        return str.replace(/[\p{P}\p{S}]/gu, "-");
      };

      let result = "";
      const add = (str) => {
        for (let i = 0; i < str.length; i++) {
          const replaceClassName = replaceSymbol(str[i].class_name);
          const className = str[i].class_name
            ? `<h2 id="${replaceClassName}"><a href="#${replaceClassName}" class="headerlink" title="${str[i].class_name}"></a>${str[i].class_name}</h2>`
            : "";
          const classDesc = str[i].class_desc
            ? `<div class="flink-desc">${str[i].class_desc}</div>`
            : "";

          let listResult = "";
          const lists = str[i].link_list;
          if (true) {
            lists.sort(() => Math.random() - 0.5);
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
          </div>`;
          }

          result += `${className}${classDesc} <div class="flink-list">${listResult}</div>`;
        }

        document
          .querySelector(".flink")
          .insertAdjacentHTML("afterbegin", result);
        window.lazyLoadInstance && window.lazyLoadInstance.update();
      };

    const linkData = [{
        "class_name": "学习网站",
        "class_desc": "Use it!",
        "link_list": [{
            "name": "JavaGuide",
            "link": "https://javaguide.cn/",
            "avatar": "https://javaguide.cn/favicon.ico",
            "descr": "「Java学习 + 面试指南」涵盖 Java 程序员需要掌握的核心知识"
        }, {
            "name": "Quick Reference",
            "link": "https://wangchujiang.com/reference/",
            "avatar": "https://cheatsheets.zip/images/favicon.png?v=1",
            "descr": "速查网站"
        }, {
            "name": "Cool-Papers",
            "link": "https://papers.cool/",
            "avatar": "https://papers.cool/static/favicon.ico",
            "descr": "顶级科研网站！"
        }]
    }, {
         "class_name": "精品课程",
         "class_desc": "博主强推的UP主！",
         "link_list": [{
             "name": "青空の霞光",
             "link": "https://space.bilibili.com/37737161/?spm_id_from=333.999.0.0",
             "avatar": "/Blog/img/ico/bilibili.png",
             "descr": "精品Java视频课程",
         }]
    }, {
        "class_name": "工具合集箱",
        "class_desc": "好用的工具合集网站",
        "link_list": [{
            "name": "UU在线工具",
            "link": "https://uutool.cn/type/history/",
            "avatar": "https://uutool.cn/assets/images/favicon.png",
            "descr": "集合超多工具的网站",
        }, {
            "name": "IT-TOOLS",
            "link": "https://it-tools.tech/",
            "avatar": "https://it-tools.tech/favicon.ico",
            "descr": "Handy tools for developers"
        }, {
            "name": "LaTex公式编辑器",
            "link": "https://www.latexlive.com/home##",
            "avatar": "/Blog/img/default_img.jpg",
            "descr": "在线LaTeX公式编辑器，支持图片识别(付费)",
        }, {
            "name": "SimpleTex",
            "link": "https://simpletex.net/ai/latex_ocr",
            "avatar": "https://simpletex.net/simpletex.ico",
            "descr": "真·免费的在线LaTeX公式编辑器，支持图片识别",
        }]
    }, {
        "class_name": "前端设计站",
        "class_desc": "值得推荐的设计网站",
        "link_list": [{
            "name": "iconfont",
            "link": "https://www.iconfont.cn/",
            "avatar": "https://img.alicdn.com/imgextra/i4/O1CN01Z5paLz1O0zuCC7osS_!!6000000001644-55-tps-83-82.svg",
            "descr": "阿里巴巴矢量图标库"
        }, {
            "name": "渐变颜色",
            "link": "https://color.oulu.me/",
            "avatar": "https://color.oulu.me/favicon.ico",
            "descr": "一个集合180种免费的线性渐变网站，可在任何网站使用"
        }, {
            "name": "彼岸图库",
            "link": "https://pic.netbian.com/4kfengjing/index_2.html",
            "avatar": "https://pic.netbian.com/favicon.ico",
            "descr": "每天一张免费背景",
        }, {
            "name": "图标抓取",
            "link": "https://gonglue.qinggl.com/app/img/icon.jsp",
            "avatar": "https://qglimg.qinglm.com/qinggl/favicon.ico",
            "descr": "网页图标在线抓取",
        }, {
            "name": "Favicon Generator",
            "link": "https://realfavicongenerator.net/",
            "avatar": "https://realfavicongenerator.net/favicon-48x48.png",
            "descr": "将图片转换为Favicon",
        }, {
            "name": "漫步白月光壁纸",
            "link": "https://wallpaper.abcb.fun/",
            "avatar": "https://wallpaper.abcb.fun/favicon.ico",
            "descr": "无限量下载高清壁纸",
        }]
    },  {
        "class_name": "文件处理馆",
        "class_desc": "高效处理你的文件",
        "link_list": [{
            "name": "CleverPDF",
            "link": "https://www.cleverpdf.com/jp",
            "avatar": "https://www.cleverpdf.com/statics/images/favicon.ico",
            "descr": "44 个强大的在线 PDF 工具，无需会员资格，永久免费！",
        }, {
            "name": "Convertio",
            "link": "https://convertio.co/zh/",
            "avatar": "https://convertio.co/favicon.ico",
            "descr": "文件转换器",
        }, {
            "name": "PHOTOKIT",
            "link": "https://photokit.com/?lang=zh",
            "avatar": "https://photokit.com/images/icon256.png",
            "descr": "基于AI人工智能的在线图片编辑器，方便易用",
        }]
    }, {
        "class_name": "AI研究所",
        "class_desc": "善用AI，提高效率",
        "link_list": [{
            "name": "ChatGPT",
            "link": "https://chatgpt.com/",
            "avatar": "/Blog/img/ico/openai.png",
            "descr": "第一款AI",
        }, {
            "name": "Kimi",
            "link": "https://kimi.moonshot.cn/",
            "avatar": "https://statics.moonshot.cn/kimi-chat/favicon.ico",
            "descr": "帮你看更大的世界",
        }, {
            "name": "豆包",
            "link": "https://www.doubao.com/chat/",
            "avatar": "https://lf-flow-web-cdn.doubao.com/obj/flow-doubao/doubao/web/logo-icon.png",
            "descr": "字节旗下AI智能助手",
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
                    

{% endraw %}
