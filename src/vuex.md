# Vuex

###### 1.主要应用于vue中管理数据状态的一个库

###### 2.通过创建一个集中的数据存储，供程序中所有组件访问

###### 3.Vuex是一个专门Vue.js应用程序开发的状态管理模式

#### 步骤:
1.安装 npm i vuex

2.store.js

- 引入vue
- 引入vuex
- 注册Vue.use(Vuex)
- 
         new Vuex.Store({
            state:{//状态,把需要在多个组件之间共享的数据放在这里,
                count:1
            }
            mutations:{//改变state的状态时调用
                方法1(state){//默认第一个参数是state,第二个参数是通过commit触发时过来的参数,没有第三个参数,
                如果需要传递一个很复杂的数据，可以放到一个对象里面通过第二个参数传过来,必须是同步函数
                    state.count++
                }
            },
            getters:{//在state中的数据的基础上，获取新数据，类似于computed
                
            },
            actions:{}//异步操作,通过dispatch触发

        })
- 抛出store
- main.js挂载到实例上
-
        new Vue({
            el:"#app",
            router,
            store,//程序中的所有组件才能来使用store(仓库)里面状态
        })

###### 每一个Vuex应用的核心就是store(仓库),store是一个容器,包含着vue应用的状态(state)
###### 修改Vuex的store中的状态的唯一方法是提交==mutations==
###### 在组件/视图里面通过this.$store.commit("方法名")来触发mutation里面的事件




# state
#### 怎么获取vuex中的数据
#### 怎么在视图/组件里面获取store里面的共享状态?
1.==this.$store.state.属性名==

2.==在组件内部用一个计算属性来获取数据==

        computed:{
            getCount(){
                return this.$store.state.属性名
            }
        }
    
3.==mapState==

它的作用:是把写在vuex.store.state中的数据直接映射到组件中计算属性中

用法:

1.在组件内部引入:
import {mapState} from "vuex"

2.在计算属性里面：

        computed:{
            ...mapState(["count","arr"])//数组里面的名字要和store里面定义的名字一样
        }

###### 3.如果计算属性还有其他的函数，则需要用,和...mapState分隔开

4.mapState是一个函数,这里就是调用这个函数，实参是一个数组["amount"],它的返回值是一个对象

5....mapState["amount"]把一个对象拆分，成为拓展运算符

# getters

###### 跟计算属性一样,getters的返回值会根据它的依赖被缓存起来,且只有当它的依赖值发生了改变才会被重新计算

###### state作为第一个参数,也可以接受getters作为第二个参数

在组件中:

##### this.$store.getters.getList

##### ...mapGetters(["getList"])

# mutations

    <button @click="addList({grade:"1611A",people:39})">点击按钮</button>
    

属性 | 不使用map辅助函数 | 使用map函数 | 使用map函数时的位置
---|---|---|---
state | this.$store.state.属性名 | ...mapState["属性名"] | 放在计算属性里
getters |this.$store.getters.方法名 | ...mapGetters(["方法名"]) | 计算属性
mutations | this.$store.commit("方法名") | ...mapMutations(["方法名"]) | 方法methods
actions | this.$store.dispatch("方法名") | ...mapActions(["方法名"]) | 方法methods

