# Protobuf introduction
protobuf是Google开发的一个序列化框架，类似XML，JSON，基于二进制，比传统的XML表示同样一段内容要短小得多。通过protobuf，可以很轻松的调用相关方法来完成业务数据的序列化与反序列化。

[来自谷歌的主要参考文献](https://developers.google.com/protocol-buffers/docs/pythontutorial)

## message形式
    message A{
        repeated string b;
        optional int32 c;
    }
    
    message D{
        required A a;
    }
    
    
