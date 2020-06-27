# tc-cloude
腾讯云开发第四章
任务一：管理端部分的列表加载变成实时数据库监听形式出发。
任务二：用户端列表加载云函数实拍超过100调的场景，采用promise all的形式进行改造，使其可以支持超过100条
开发思路：
任务一思路：1、将管理端列表代码锁定。webviews/ admin.html-> webviews/asset/admin.js ->initlist() 函数，找到调用云函数代码。
          2、修改initlist()代码 。修改列表实现，为数据库监听。
任务二思路：1、锁定待修改文件，平台反馈列表文件; webviews/index.html -> webviews/asset/index.js ->  cloudfunctions/init/index.js init 云函数
          2、调用init云函数代码修改。在webviews/index.js中修改
          cloud.callFunction({
           name: 'init'
          })
          .then((res) => {
              refreshlist(res.result.list);
          });
          3、修改cloudfunctions/init/index.js 中云函数的实现 ， 使用Promise。all
           
          
