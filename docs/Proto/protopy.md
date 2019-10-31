# Protobuf in python

## 编辑message的方式
对于addressbook.proto文件中的message：

    message Person {
      required string name = 1;
      required int32 id = 2;
      optional string email = 3;

      enum PhoneType {
        MOBILE = 0;
        HOME = 1;
        WORK = 2;
      }

      message PhoneNumber {
        required string number = 1;
        optional PhoneType type = 2 [default = HOME];
      }

      repeated PhoneNumber phones = 4;
    }

    message AddressBook {
      repeated Person people = 1;
    }
       
生成为python所识别的文件addressbook_pb2.py

使用以下的方式添加各个元素：

    import addressbook_pb2
    person = addressbook_pb2.Person()
    person.id = 1234
    person.name = "John Doe"
    person.email = "jdoe@example.com"
    phone = person.phones.add()
    phone.number = "555-4321"
    phone.type = addressbook_pb2.Person.PhoneType.HOME
    
