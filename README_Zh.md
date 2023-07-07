# axupimgs

[![npm version](https://img.shields.io/npm/v/axupimgs.svg?style=flat-square)](https://www.npmjs.org/package/axupimgs)

🌏 [English](https://github.com/Kori000/axupimgs/blob/main/README.md)

## 功能

- Tinymce 多图上传 插件

### 介绍

- 原作者: 莫若卿
- Tinymce 版本支持: 5.0.4+
- 支持语言: 简体中文
- 仓库作者: Kori

### 使用

- 将本库文件夹 (axupimgs) 放到 TinyMCE 主目录下的 plugins 文件夹内

- 路径样例: **public/js/tinymce/plugins/axupimgs**

- 在你的组件页面中:
  - **many_images_upload_handler** 为此插件上传逻辑
  - **blobInfo** 是文件信息
  - **succFun** 是成功返回的 url
  - **failFun** 是错误返回的 消息

```js
 initTinymce() {
      const _this = this
      window.tinymce.init({
        selector: `#tinymceId`,
        plugins: 'axupimgs',
        toolbar: [
          'axupimgs'
        ],
        width: '100%',
        fontsize_formats: '12px 14px 16px 18px 20px 22px 24px 26px 36px 48px 56px',
        statusbar: false,
        // images_upload_handler: (blobInfo) => {
        // },
        // you need define this 'many_images_upload_handler'
        many_images_upload_handler: (blobInfo, succFun, failFun) => {
          // uploadApi is network api
          const res = uploadApi(blobInfo)
          if (res) {
            succFun(res.url)
          } else {
            failFun('fail error')
          }
        },


      })
    },
```
