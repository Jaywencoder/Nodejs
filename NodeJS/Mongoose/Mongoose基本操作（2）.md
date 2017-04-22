# Mongodb 的基本操作（2）

```
1.find查询： obj.find(查询条件,callback);

Model.find({},function(error,docs){
   //若没有向find传递参数，默认的是显示所有文档
});

Model.find({ "age": 28 }, function (error, docs) {
  if(error){
    console.log("error :" + error);
  }else{
    console.log(docs); //docs: age为28的所有文档
  }
}); 

2. Model.create(文档数据, callback))

Model.create({ name:"model_create", age:26}, function(error,doc){
    if(error) {
        console.log(error);
    } else {
        console.log(doc);
    }
});

3. Entity.save(文档数据, callback))

var Entity = new Model({name:"entity_save",age: 27});

Entity.save(function(error,doc) {
    if(error) {
        console.log(error);
    } else {
        console.log(doc);
    }
});

4. obj.update(查询条件,更新对象,callback);

var conditions = {name : 'test_update'};

var update = {$set : { age : 16 }};

TestModel.update(conditions, update, function(error){
    if(error) {
        console.log(error);
    } else {
        console.log('Update success!');
    }
});

5. obj.remove(查询条件,callback);

var conditions = { name: 'tom' };

TestModel.remove(conditions, function(error){
    if(error) {
        console.log(error);
    } else {
        console.log('Delete success!');
    }
});

使用$gt(>)、$lt(<)、$lte(<=)、$gte(>=)操作符进行排除性的查询，如下示例：

Model.find({"age":{"$gt":18}},function(error,docs){
   //查询所有nage大于18的数据
});

Model.find({"age":{"$lt":60}},function(error,docs){
   //查询所有nage小于60的数据
});

Model.find({"age":{"$gt":18,"$lt":60}},function(error,docs){
   //查询所有nage大于18小于60的数据
});

$ne(!=)操作符的含义相当于不等于、不包含，查询时我们可通过它进行条件判定，具体使用方法如下：

Model.find({ age:{ $ne:24}},function(error,docs){
    //查询age不等于24的所有数据
});

Model.find({name:{$ne:"tom"},age:{$gte:18}},function(error,docs){
  //查询name不等于tom、age>=18的所有数据
});

和$ne操作符相反，$in相当于包含、等于，查询时查找包含于指定字段条件的数据。具体使用方法如下：

Model.find({ age:{ $in: 20}},function(error,docs){
   //查询age等于20的所有数据
});

Model.find({ age:{$in:[20,30]}},function(error,docs){
  //可以把多个值组织成一个数组
}); 

$or操作符，可以查询多个键值的任意给定值，只要满足其中一个就可返回，用于存在多个条件判定的情况下使用，如下示例：

Model.find({"$or":[{"name":"yaya"},{"age":28}]},function(error,docs){
  //查询name为yaya或age为28的全部文档
});

$exists操作符，可用于判断某些关键字段是否存在来进行条件查询。如下示例

Model.find({name: {$exists: true}},function(error,docs){
  //查询所有存在name属性的文档
});

Model.find({telephone: {$exists: false}},function(error,docs){
  //查询所有不存在telephone属性的文档
});

结果排序：find(Conditions,fields,options,callback);

Model.find({},null,{sort:{age:-1}},function(err,docs){
  //查询所有数据，并按照age降序顺序返回数据docs
});

限制数量：find(Conditions,fields,options,callback);

Model.find({},null,{limit:20},function(err,docs){
    console.log(docs);
});

跳过数量：find(Conditions,fields,options,callback);

Model.find({},null,{skip:4},function(err,docs){
    console.log(docs);
});

Schema添加属性值
var mongoose = require('mongoose');

var TempSchema = new mongoose.Schema;

TempSchema.add({ name: 'String', email: 'String', age: 'Number' });```
转自：http://blog.csdn.net/u010957293/article/details/51649551