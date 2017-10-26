#### 简述
JQuery 事件操作方式大致相似,在这里就列举一个 mousemove 事件, 其他的事件可以类比使用  




    方法一：$ele.mousemove()
    
    绑定$ele元素，不带任何参数一般是用来指定触发一个事件，用的比较少
    
    <div id="test">点击触发<div>
    $("ele").mousemove(function(){
        alert('触发指定事件')
    })
    $("#test").click(function(){
         $("ele").mousemove()  //指定触发事件 
    });
     

-------

    方法二：$ele.mousemove( handler(eventObject) )
    
    绑定$ele元素，每次$ele元素触发点击操作会执行回调 handler函数
    
    这样可以针对事件的反馈做很多操作了
    
    <div id="test">滑动触发<div>
    $("#test").mousemove(function() {
        //this指向 div元素 
    });

-------
     
    
    方法三：$ele.mousemove( [eventData ], handler(eventObject) )
    
    使用与方法二一致，不过可以接受一个数据参数，这样的处理是为了解决不同作用域下数据传递的问题
    
    <div id="test">点击触发<div>
    $("#test").mousemove(11111,function(e) {
        //this指向 div元素
        //e.data  => 11111 传递数据
    });
     

#### mousemove事件触发需要以下几点：

    mousemove事件是当鼠标指针移动时触发的，即使是一个像素
    如果处理器做任何重大的处理，或者如果该事件存在多个处理函数，这可能造成浏览器的严重的性能问题


#### 代码如下

    
    <!DOCTYPE html>
    <html>
    
    <head>
        <meta http-equiv="Content-type" content="text/html; charset=utf-8"/>
        <title></title>
        <style>
            .left div,
            .right div {
                width: 300px;
                height: 80px;
                padding: 5px;
                margin: 5px;
                border: 1px solid #ccc;
            }
    
            .left div {
                background: #bbffaa;
            }
    
            .right div {
                background: yellow;
            }
        </style>
        <script src="http://libs.baidu.com/jquery/1.9.1/jquery.js"></script>
    </head>
    
    <body>
    <h2>.mousemove()方法</h2>
    <h4>测试一</h4>
    <button>点击：指定触发mousemove事件</button>
    <script type="text/javascript">
        $('h2').mousemove(function (e) {
            alert('触发h2元素绑定的mousemove')
        })
    
        $("button:eq(0)").click(function (e) {
            $('h2').mousemove() //指定触发绑定的事件
        })
    </script>
    
    
    <h4>测试二</h4>
    <div class="left">
        <div class="aaron1">
            <p>鼠标在绿色区域移动触发mousemove</p>
            <p>移动的X位置：</p>
        </div>
    </div>
    <script type="text/javascript">
        //绑定一个mousemove事件
        //触发后修改内容
        $(".aaron1").mousemove(function (e) {
            $(this).find('p:last').html('移动的X位置：' + e.pageX)
        })
    </script>
    
    
    <h4>测试三</h4>
    <div class="right">
        <div class="aaron3">
            <p>鼠标移动：不同函数传递数据</p>
            <p>数据：</p>
        </div>
    </div>
    <script type="text/javascript">
        //不同函数传递数据
        function data(e) {
            $(this).find('p:last').html('数据:' + e.data)
        }
    
        function a() {
            $(".right").mousemove(1111, data)
        }
        a();
    </script>
    </body>
    
    </html>
    
    

总结:
Jquer 事件处理方式大致相同 , 使用的时候可以参考[手册](http://hemin.cn/jq/index.html) 做到举一反三 

