---
title: Xbox-Game-Pass-List  （5/5）
date: 2024-01-07
---
{% raw %}
<style>
    .table-container {
    overflow: none;
  }
  table {
    border-collapse: collapse;
    border-spacing: 0;
    font-size: 0.875em;
    margin: 0 0 0 0;
  }
  tbody tr:nth-of-type(odd) {
    background: var(--table-row-odd-bg-color);
  }
  tbody tr:hover {
    background: var(--table-row-hover-bg-color);
  }
  caption,
  th,
  td {
    font-weight: normal;
    padding: none;
    text-align: left;
    vertical-align: middle;
  }
  th,
  td {
    border: 0;
    border-bottom: none;
  }
  th {
    font-weight: 700px;
    padding-bottom: none;
  }
  td {
    border-bottom-width: none;
  }
  .title_main_r {
    background: #333;
    width: 400px;
    height: 80px;
    padding: 0px;
  }
  .title_cn_r {
    color: #f0f0f0;
    text-align: left;
    font-weight: bold;
    font-size: 32px;
    line-height: 32px;
    padding-top: 5px;
    padding-left: 7px;
  }
  .type_a_r {
    width: 100px;
    height: 40px;
    text-align: center;
    background: #ce0000;
    color: #f0f0f0;
    font-size: 18px;
    line-height: 32px;
    padding: 0px;
  }
  .type_tag_r1 {
    width: 100px;
    text-align: center;
    background: #c0c0c0;
    color: #003;
    font-size: 12px;
    line-height: 18px;
    padding: 0px;
  }
  .staff_r1 {
    width: 250px;
    text-align: left;
    vertical-align: top;
    font-size: 16px;
    line-height: 18px;
    padding: 0px;
    padding-top: 5px;
    padding-left: 5px;
  }
  .cast_r {
    width: 190px;
    text-align: left;
    vertical-align: top;
    font-size: 16px;
    line-height: 18px;
    padding: 0px;
    padding-top: 5px;
    padding-left: 0px;
  }
  .link_a_r {
    width: 100px;
    text-align: center;
    vertical-align: middle;
    font-size: 16px;
    line-height: 24px;
    padding: 0px;
  }
</style>

{% endraw %}

<span style="display:block;text-align:center;">以下为今日XGP会员商店游戏展示</span>
**当前游戏共** **<u>458</u>** 部

<div class="card"></div>

{% raw %}
<script>
    document.addEventListener('DOMContentLoaded', () => {
    const jsonDataUrl = '/data/game.json';
    const cardContainer = document.querySelector('.card');

    fetch(jsonDataUrl)
        .then(response => {
            if (!response.ok) {
                throw new Error(`HTTP error! Status: ${response.status}`);
            }
            return response.json();
        })
        .then(data => {
            // 分页显示，假设每页显示100个
            const itemsPerPage = 100;
            const totalItems = data.length;

            // 计算总页数
            const totalPages = Math.ceil(totalItems / itemsPerPage);

            // 模拟当前页面
            const currentPage = 5;

            // 计算起始和结束位置
            const startIndex = (currentPage - 1) * itemsPerPage;
            const endIndex = Math.min(currentPage * itemsPerPage, totalItems);

            // 获取当前页面的数据
            const dataToRender = data.slice(startIndex, endIndex);
            // 遍历数据，为每个对象调用 renderCard 函数
            dataToRender.forEach(item => {
                renderCard(item);
            });
        })
        .catch(error => {
            console.error('Error fetching JSON:', error);
        });



    // 生成 HTML 片段的函数
    function renderCard(jsonData) {
            const cardHTML = `
                <div style="clear: both;"></div>
                <div style="float:left">
                    <a class="fancybox fancybox.image" href="${jsonData.images.Poster[0]+"?w=180"}" itemscope="" itemtype="http://schema.org/ImageObject" itemprop="url" data-fancybox="default" rel="default">
                    <img width="180px" src="${jsonData.images.Poster[0]+"?w=180"}" referrerpolicy="no-referrer">
                    </a>
                </a>
                </div>
                <div>
                    <div class="table-container">
                        <table width="600px">
                            <tbody>
                                <tr>
                                    <td class="title_main_r" colspan="2" rowspan="2">
                                        <p class="title_cn_r">${jsonData.productTitle}</p>
                                    </td>
                                    <td class="type_a_r">游戏类型</td>
                                </tr>
                                <tr>
                                    <td class="type_tag_r1">${jsonData.categories[0]}</td>
                                </tr>
                                <tr>
                                    <td rowspan="2" class="staff_r1">
                                        <span style="line-height: 2;">开发商: ${jsonData.developerName}</span><br>
                                        <span style="line-height: 2;">发行商: ${jsonData.publisherName}</span><br>
                                        <span style="line-height: 2;">发行日期: ${jsonData.releaseDate}</span><br>
                                        <span style="line-height: 2;">用户评分: ${jsonData.userRating}</span><br>
                                        <span style="line-height: 2;">售价: ${jsonData.pricing.ListPrice} ${jsonData.pricing.currencyCode}</span><br>
                                    </td>
                                    <td rowspan="2" class="cast_r">
                                        太长了先不写了
                                    </td>
                                    <td class="link_a_r">
                                        <a href="${jsonData.storePage}" target="_blank">商店页面</a><br>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            `;

            // 将生成的 HTML 添加到页面中的某个元素
    cardContainer.innerHTML += cardHTML;
    }
})

</script>
{% endraw %}