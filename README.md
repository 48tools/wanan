# 晚安生成器FE

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


### Note
还在继续开发中，预计下周完成（咕咕咕）。

浏览器内预览

```javascript
var img = new Image();
document.body.appendChild(img);
html2canvas(component.$refs.wanan.$el, { useCORS:true, scale: 2 }).then(function(canvas) {
  document.body.appendChild(canvas);
  img.src = canvas.toDataURL('image/jpeg', 1);
});
```
