<template>
  <div class="main markdown">
    <ul class="icon_lists clear"  >
      <li>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-Database_maintain1"></use>
        </svg>
        <div class="name">数据库维护服务</div>
      </li>

      <li>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-chimney"></use>
        </svg>
        <div class="name">chimney</div>
      </li>

      <li>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-sugar"></use>
        </svg>
        <div class="name">sugar</div>
      </li>
      <li v-for="item in icons[0].icon" >
        <svg class="icon" aria-hidden="true" @click="select(item.icon)">
          <use :xlink:href="'#'+item.icon"></use>
        </svg>
        <div class="name"> {{ item.name }}</div>
      </li>
    </ul>
  </div>
</template>

<script>
import icons from './data/index'
export default {
  name: 'wc-icon-select',
  data () {
    return {
      // 绑定弹出框
        selectIcon: '',
        icons,
    }
  },
  computed: {
  },
  methods: {
    select(icon){
        //获取点击对象
        this.selectIcon = icon;
        this.$emit("setIcon",icon);
    },
    selectIcon (iconName = '') {
      this.$emit('input', iconName)
      if (iconName && this.autoClose) {
        this.pop = false
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  .icon {
    /* 通过设置 font-size 来改变图标大小 */
    width: 1em; height: 1em;
    /* 图标和文字相邻时，垂直对齐
    vertical-align: -0.15em; */
    /* 通过设置 color 来改变 SVG 的颜色/fill */
    fill: currentColor;
    /* path 和 stroke 溢出 viewBox 部分在 IE 下会显示
       normalize.css 中也包含这行 */
    overflow: hidden;
    height:100px;margin:0;
    cursor: pointer;
  }



  /** 重置文本格式元素 **/
  a { text-decoration: none; }
  a:hover { text-decoration: underline; }


  /** 重置表单元素 **/
  legend { color: #000; } /* for ie6 */
  fieldset, img { border: 0; } /* img 搭车：让链接里的 img 无边框 */
  button, input, select, textarea { font-size: 100%; } /* 使得表单元素在 ie 下能继承字体大小 */
  /* 注：optgroup 无法扶正 */

  /** 重置表格元素 **/
  table { border-collapse: collapse; border-spacing: 0; }

  /* 清除浮动 */
  .ks-clear:after, .clear:after {
    content: '\20';
    display: block;
    height: 0;
    clear: both;
  }
  .ks-clear, .clear {
    *zoom: 1;
  }

  .main {
    padding: 0px 0px;
    margin: 0 auto;
  }
  .main h1{font-size:36px; color:#333; text-align:left;margin-bottom:30px; border-bottom: 1px solid #eee;}

  .helps{margin-top:40px;}
  .helps pre{
    padding:20px;
    margin:10px 0;
    border:solid 1px #e7e1cd;
    background-color: #fffdef;
    overflow: auto;
  }

  .icon_lists{
    width: 100% !important;

  }

  .icon_lists li{
    float:left;
    width: 100px;
    height:180px;
    text-align: center;
    list-style: none !important;
  }
  .icon_lists .icon{
    font-size: 42px;
    line-height: 100px;
    margin: 10px 0;
    color:#333;
    -webkit-transition: font-size 0.25s ease-out 0s;
    -moz-transition: font-size 0.25s ease-out 0s;
    transition: font-size 0.25s ease-out 0s;

  }
  .icon_lists .icon:hover{
    font-size: 100px;
  }

  .markdown {
    color: #666;
    font-size: 14px;
    line-height: 1.8;
  }

  .markdown > ul{
    padding: 0 10px 0 0;
    margin: 0;
  }
  .highlight {
    line-height: 1.5;
  }

  .markdown img {
    vertical-align: middle;
    max-width: 100%;
  }

  .markdown h1 {
    color: #404040;
    font-weight: 500;
    line-height: 40px;
    margin-bottom: 24px;
  }

  .markdown h2,
  .markdown h3,
  .markdown h4,
  .markdown h5,
  .markdown h6 {
    color: #404040;
    margin: 1.6em 0 0.6em 0;
    font-weight: 500;
    clear: both;
  }

  .markdown h1 {
    font-size: 28px;
  }

  .markdown h2 {
    font-size: 22px;
  }

  .markdown h3 {
    font-size: 16px;
  }

  .markdown h4 {
    font-size: 14px;
  }

  .markdown h5 {
    font-size: 12px;
  }

  .markdown h6 {
    font-size: 12px;
  }

  .markdown hr {
    height: 1px;
    border: 0;
    background: #e9e9e9;
    margin: 16px 0;
    clear: both;
  }

  .markdown p,
  .markdown pre {
    margin: 1em 0;
  }

  .markdown > p,
  .markdown > blockquote,
  .markdown > .highlight,
  .markdown > ol,
  .markdown > ul {
    width: 80%;
  }

  .markdown ul > li {
    list-style: circle;
  }

  .markdown > ul li,
  .markdown blockquote ul > li {
    margin-left: 20px;
    padding-left: 4px;
  }

  .markdown > ul li p,
  .markdown > ol li p {
    margin: 0.6em 0;
  }

  .markdown ol > li {
    list-style: decimal;
  }

  .markdown > ol li,
  .markdown blockquote ol > li {
    margin-left: 20px;
    padding-left: 4px;
  }

  .markdown code {
    margin: 0 3px;
    padding: 0 5px;
    background: #eee;
    border-radius: 3px;
  }

  .markdown pre {
    border-radius: 6px;
    background: #f7f7f7;
    padding: 20px;
  }

  .markdown pre code {
    border: none;
    background: #f7f7f7;
    margin: 0;
  }

  .markdown strong,
  .markdown b {
    font-weight: 600;
  }

  .markdown > table {
    border-collapse: collapse;
    border-spacing: 0px;
    empty-cells: show;
    border: 1px solid #e9e9e9;
    width: 95%;
    margin-bottom: 24px;
  }

  .markdown > table th {
    white-space: nowrap;
    color: #333;
    font-weight: 600;

  }

  .markdown > table th,
  .markdown > table td {
    border: 1px solid #e9e9e9;
    padding: 8px 16px;
    text-align: left;
  }

  .markdown > table th {
    background: #F7F7F7;
  }

  .markdown blockquote {
    font-size: 90%;
    color: #999;
    border-left: 4px solid #e9e9e9;
    padding-left: 0.8em;
    margin: 1em 0;
    font-style: italic;
  }

  .markdown blockquote p {
    margin: 0;
  }

  .markdown .anchor {
    opacity: 0;
    transition: opacity 0.3s ease;
    margin-left: 8px;
  }

  .markdown .waiting {
    color: #ccc;
  }

  .markdown h1:hover .anchor,
  .markdown h2:hover .anchor,
  .markdown h3:hover .anchor,
  .markdown h4:hover .anchor,
  .markdown h5:hover .anchor,
  .markdown h6:hover .anchor {
    opacity: 1;
    display: inline-block;
  }

  .markdown > br,
  .markdown > p > br {
    clear: both;
  }


  .hljs {
    display: block;
    background: white;
    padding: 0.5em;
    color: #333333;
    overflow-x: auto;
  }

  .hljs-comment,
  .hljs-meta {
    color: #969896;
  }

  .hljs-string,
  .hljs-variable,
  .hljs-template-variable,
  .hljs-strong,
  .hljs-emphasis,
  .hljs-quote {
    color: #df5000;
  }

  .hljs-keyword,
  .hljs-selector-tag,
  .hljs-type {
    color: #a71d5d;
  }

  .hljs-literal,
  .hljs-symbol,
  .hljs-bullet,
  .hljs-attribute {
    color: #0086b3;
  }

  .hljs-section,
  .hljs-name {
    color: #63a35c;
  }

  .hljs-tag {
    color: #333333;
  }

  .hljs-title,
  .hljs-attr,
  .hljs-selector-id,
  .hljs-selector-class,
  .hljs-selector-attr,
  .hljs-selector-pseudo {
    color: #795da3;
  }

  .hljs-addition {
    color: #55a532;
    background-color: #eaffea;
  }

  .hljs-deletion {
    color: #bd2c00;
    background-color: #ffecec;
  }

  .hljs-link {
    text-decoration: underline;
  }

  pre{
    background: #fff;
  }

</style>
