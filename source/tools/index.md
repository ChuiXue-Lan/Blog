---
title: 工具网站
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
            "name": "IT-TOOLS",
            "link": "https://it-tools.tech/",
            "avatar": "https://it-tools.tech/favicon.ico",
            "descr": "Handy tools for developers"
        }]
    },  {
        "class_name": "工具合集箱",
        "class_desc": "好用的工具合集网站",
        "link_list": [{
            "name": "UU在线工具",
            "link": "https://uutool.cn/type/history/",
            "avatar": "https://uutool.cn/assets/images/favicon.png",
            "descr": "集合超过工具的网站",
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
            "name": "hatchful",
            "link": "https://www.shopify.com/zh/tools/logo-maker",
            "avatar": "https://cdn.shopify.com/static/shopify-favicon.png",
            "descr": "免费的logo制作器"
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
            "name": "Logo设计",
            "link": "https://www.canva.cn/logos/",
            "avatar": "https://www.canva.cn/favicon.ico",
            "descr": "在线制作Logo",
        }, {
            "name": "DesignEvo",
            "link": "https://www.designevo.com/cn/",
            "avatar": "/Blog/img/default_img.jpg",
            "descr": "在线制作Logo",
        }, {
            "name": "Favicon Generator",
            "link": "https://realfavicongenerator.net/",
            "avatar": "https://realfavicongenerator.net/the_favicon/apple-touch-icon.png?v=zX7n49rwEM",
            "descr": "将图片转换为Favicon",
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
            "name": "敬请期待...",
            "link": "https://www.baidu.com/",
            "avatar": "/Blog/img/default_img.jpg",
            "descr": "敬请期待...",
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
