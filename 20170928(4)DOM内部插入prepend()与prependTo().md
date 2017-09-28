#  简述
    在元素内部进行操作的方法，除了在被选元素的结尾（仍然在内部）通过append与appendTo插入指定内容外，相应的还可以在被选元素之前插入，jQuery提供的方法是prepend与prependTo



# 代码  


    <!DOCTYPE html>
    <html>
    
    <head>
        <meta http-equiv="Content-type" content="text/html; charset=utf-8" />
        <title></title>
        <script src="http://lib.sinaapp.com/js/jquery/1.9.1/jquery-1.9.1.min.js"></script>
        <style>
        .aaron1{
            border: 1px solid red;
        }
        .aaron1 p {
            color: red;
        }
        .aaron2{
            border: 1px solid blue;
        }
        .aaron2 p {
            color: blue;
        }
        </style>
    </head>
    
    <body>
        <h2>通过prepend与prependTo添加元素</h2>
        <button id="bt1">点击通过jQuery的prepend添加元素</button>
        <button id="bt2">点击通过jQuery的prependTo添加元素</button>
        <div class="aaron1">
            <p>测试prepend</p>
        </div>
        <div class="aaron2">
            <p>测试prependTo</p>
        </div>
        <script type="text/javascript">
        $("#bt1").on('click', function() {
            //找到class="aaron1"的div节点
            //然后通过prepend在内部的首位置添加一个新的p节点
            $('.aaron1')
                .prepend('<p>prepend增加的p元素</p>')
        })
        </script>
        <script type="text/javascript">
        $("#bt2").on('click', function() {
            //找到class="aaron2"的div节点
            //然后通过prependTo内部的首位置添加一个新的p节点
            $('<p>prependTo增加的p元素</p>')
                .prependTo($('.aaron2'))
        })
        </script>
    </body>
    
    </html>






#     这里总结下内部操作四个方法的区别：

    * append()向每个匹配的元素内部追加内容
    * prepend()向每个匹配的元素内部前置内容
    * appendTo()把所有匹配的元素追加到另一个指定元素的集合中
    * prependTo()把所有匹配的元素前置到另一个指定的元素集合中

