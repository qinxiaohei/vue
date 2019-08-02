####  1.vue是一个渐进式框架，轻量，易于上手。
 
####  2.vue是一个MVVM的一个框架。

    M(数据层)

    V(视图)
    
    VM(数据双向绑定)
    
#### 3.实例化

- 接受的是一个对象

new Vue({
    
    el:"#app",//把vue实例挂在到那个元素上边，一般情况下一个页面只有一个实例，所以用的是id选择器(内部挂载元素)
    
    template:`<span>999</span>` , //模板字符串，会替换挂载元素("#app")
    
    data:数据,//是一个对象
    
    watch:{//侦听器,监听的属性必须是data里挂载过的值
    
        name(news,old){//第一个参数是新值，第二个参数是老值
            
        }
        
    },
    
    computed:{//计算属性(属性不需要卸载data里)
    
        //只有数据没变，就只执行一次，一直不会发生变化
        
        //当计算属性所依赖的数据发生变化的时候,会重新计算属性
        
        //所依赖的数据为data里的数据
        
        //缓存属性
        
        price(){//获取属性
            
        }
        
        price:{//需要设置值的时候,用对象的这种形式
            
            get(){
                
            },
            set(val){
                
                console.log(val,"123")
                
            }
        }
    },
    
    methods:{
    
        方法名1(){
        
            //this指的是当前的实例
        },
        
        方法名2(){
            
        }
    },
    
    beforeCreate(){//初始化,收集配置项
    
        console.log("beforeCreate")
        
        console.log(this.$el,this.$data)//都拿不到
        
    },
    
    created(){//分配配置项到实例上边
    
        console.log(this.$el)//拿不到this.$el
        
        console.log(this.$data)//能拿到
        
    },
    
    beforeMount(){//template里面的东西生成DOM节点之前
        
        //开始执行beforeMount挂载钩子，注意此时还没有生成html到页面上
        
    },
    
    mounted(){//生成DOM节点
    
        //挂载完成,也就是模板中的html渲染到了html页面中,此事一般可以做一些ajax操作,mounted只会执行一次!!!!!
        
    },
    
    beforeUpdate(){//数据更新之前触发
    
        console.log(this.$refs)  //获取页面里面所有有ref属性的dom
        
        console.log(this.$refs.grade.innerHTML)
        
    },
    
    updated(){//数据更新的时候触发
        
        
    }
    
    
    
})

## window.vm = vm
## vm.$mount("#app")//外部挂载元素
## vm.$watch("name",(news,old)=>{
     console.log(news,old)
 }()
- 配置项里面名称不能修改
- 获取data里面的数据时,vm.数据名
- {{}}放在双标签里面

#### 4.指令  v-

- ==v-text==  

    //只能解析文本，解析出来的文本作为标签的内容 == {{}}
- ==v-html==    

     //解析标签
- ==v-show== 

     //控制元素的显示和隐藏，通过控制display:none/block来实现的
- ==v-on:eventname== 
 
     //绑定事件  

    简写:@eventname

    eventname :click keyup input change

- ==v-bind==:属性名    //绑定动态属性  简写  ：属性名

        属性名 = "变量名"  //按字符串解析的

        :属性名 = "变量名"  //按变量解析
   
- ==v-for== 
 
     //循环

    1.循环对象：(value,key,index) in obj

        第一个是对象里面每一项value,第二个是对象里面每一项的key,，第三个是下标
    
    2.循环数组:(item,index,key) in list
    
        第一个是数组里面的每一项,第二个是下标，第三个没用
        
    3.循环数字:(item,index,key) in Number
    
        第一个是从1开始的一个整数，第二个是下标，第三个没用

- ==$event== 事件对象

- ==v-model== 实现双向绑定，一般用在表单元素上
 
- ==v-cloak== 
     
    元素上直到关联实例结束编译，(编译结束之后再展示)

    这个指令需要配合着display:none一起使用： 
    
         [v-cloak]{
         
             display:none;
             
         }
     
- ==v-pre== 会跳过这个元素和他的子元素的编译过程

- ==v-if== 控制元素显示和隐藏，条件不满足，不会创建节点

- ==v-else-if==  ==v-else== 
 
    这两个指令要配合着v-if一起使用，

    如果要平凡的操作DOM，建议使用==v-show==

#### @eventname.修饰符

1.==prevent==     //阻止默认事件

2.==stop==   //阻止冒泡

3.==self== //只触发自身的事件

4.==capture== //捕获阶段触发的

5.==once== //只触发一次

6.==left== //鼠标左键触发

7.==right==   //鼠标右键触发

8.==middle==   //鼠标中键触发

9.==keyCode/keyalias==    //键盘状态码/键盘别名

#### ==:style==  
数组，多个样式对象应用到同一个元素上，对象:{属性名:变量}






