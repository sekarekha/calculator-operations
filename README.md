# calculator-operations
var exports = module.exports;
exports.add = function(a,b){
    return a+b;
}
exports.sub = function(a,b){
    return a-b;

}
exports.mul= function(a,b){
    return a*b;

}
exports.div = function(a,b){
    return a/b;
}
----------------------------------------------
var _cal1 = require('./cal');
var express = require('express');
var app = express();
var port = 8700;
var bodyparser = require('body-parser')
app.use(bodyparser.json());
app.use(bodyparser.urlencoded({extended:true}))
app.get('/calculator/add',function(req,res)
{
    var rs ;
    var num1 = parseInt(req.query.num1);
    var num2 = parseInt(req.query.num2);
    rs = _cal1.add(num1,num2)
    res.json(rs);
    
})
 app.get('/calculator/sub',function(req,res)
{
  var rs ;
  var a = parseInt(req.query.a);
  var b = parseInt(req.query.b);
  rs = _cal1.sub(a,b);
  res.json(rs);
})
app.get('/calculator/multiply',function(req,res)
{
  var rs 
  var a = parseInt(req.query.a);
  var b = parseInt(req.query.b);
  rs = _cal1.mul(a,b);
  res.json(rs);
})
app.get('/calculator/division',function(req,res)
{
  var rs = 0;
  var a = parseInt(req.query.a);
  var b = parseInt(req.query.b);
  rs = _cal1.div(a,b);
  res.json(rs);
})
 app.listen(port,function(err)
{
    if(err) throw err;
    console.log('server is running'+port)
}
)
