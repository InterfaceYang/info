# JsonP

```js
function ajax(params) {   

  params = params || {};   

  params.data = params.data || {};   

  var json = params.jsonp ? jsonp(params) : json(params);      



  // jsonp请求   

  function jsonp(params) {   

    //创建script标签并加入到页面中   

    var callbackName = params.jsonp;   

    var head = document.getElementsByTagName('head')[0];   

    // 设置传递给后台的回调参数名   

    params.data['callback'] = callbackName;   

    var data = formatParams(params.data);   

    var script = document.createElement('script');   

    head.appendChild(script);    

 

    //创建jsonp回调函数   

    window[callbackName] = function(json) {   

      head.removeChild(script);   

      clearTimeout(script.timer);   

      window[callbackName] = null;   

      params.success && params.success(json);   

    };    



    //发送请求   

    script.src = params.url + '?' + data;    



    //为了得知此次请求是否成功，设置超时处理   

    if(params.time) {   

     script.timer = setTimeout(function() {   

       window[callbackName] = null;   

       head.removeChild(script);   

       params.error && params.error({   

         message: '超时'   

       });   

     }, time);   

    }   

  };    



  //格式化参数   

  function formatParams(data) {   

    var arr = [];   

    for(var name in data) {   

      arr.push(encodeURIComponent(name) + '=' + encodeURIComponent(data[name]));   

    };   



    // 添加一个随机数，防止缓存   

    arr.push('v=' + random());   

    return arr.join('&');   

  }   



  // 获取随机数   

  function random() {   

    return Math.floor(Math.random() * 10000 + 500);   

  } }

著作权归作者所有。
商业转载请联系作者获得授权,非商业转载请注明出处。
原文: https://laixiazheteng.com/article/page/id/AASiankfBJWp © ghmagical.com
```

