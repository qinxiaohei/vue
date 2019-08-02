
- 获取数据
    
    接口地址：http://jsonplaceholder.typicode.com/todos
    
    接口说明：获取数据
    
    接口请求方式：get

   
    
 - 添加数据接口
    
    接口地址：http://jsonplaceholder.typicode.com/todos

    接口说明：获取数据
    
    接口请求方式：post
    
    接口请求参数：
    
    ```
        title: 标题
        completed: 是否完成 （true:已完成，false未完成）
        userId: 用户id
        id: 数据id
        
    ```
- 修改数据接口
    
    接口地址：http://jsonplaceholder.typicode.com/todos
    
    eg: 请求方式如下：
    
    axios.put(`http://jsonplaceholder.typicode.com/todos/${obj.id}`,obj)

    接口说明：修改数据
    
    接口请求方式：put
    
    接口请求参数： 
        
    
       ```
        id: 数据id,
        item: 要修改的数据
        
    ```
-  删除数据接口

    接口地址：http://jsonplaceholder.typicode.com/todos/id
     
    接口说明：删除数据
    
    接口请求方式：delete
    
    接口请求参数： 
        
    
    ```
        id: 要删除的数据id
        
    ```

-  查询数据

    接口地址：http://jsonplaceholder.typicode.com/todos/
    
    
     eg: 请求方式如下：
     
     axios.get('http://jsonplaceholder.typicode.com/todos?_limit='+count)
    
    接口说明：查询数据
    
    接口请求方式：get
    
      接口请求参数： 
        
    
    ```
        count: 要查询数据的条数
        
    ```