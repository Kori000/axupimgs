# axupimgs

[![npm version](https://img.shields.io/npm/v/axupimgs.svg?style=flat-square)](https://www.npmjs.org/package/axupimgs)

👀 [中文文档](https://github.com/Kori000/axupimgs/blob/main/README_Zh.md)

## Feature

- Tinymce Plugin - Upload multiple images

### Description

- Original author: 莫若卿
- Tinymce version support: 5.0.4+
- Supported language: Simplified Chinese
- Repo Author: Kori

### Usage

- Put this repo folder(axupimgs) in the plugins folder under the TinyMCE home directory

- Example path: **public/js/tinymce/plugins/axupimgs**

- In your component page:
  - **many_images_upload_handler** is upload logic function
  - **blobInfo** is file blob
  - **succFun** is success callback url
  - **failFun** is error message

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
