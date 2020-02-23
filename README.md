#### getBoundingClientRect
> 返回四个值
* left:元素相对于左上角视口的横向距离
* top:元素相对于左上角视口的纵向距离
* width:元素宽度
* height:元素高度
> 注意 left 和 top 不是相对于父元素左上角的距离，是相对于浏览器左上角的距离

> getBoundingClientRect()能返回的top表示的是到窗口顶部的距离，不是到文档顶部的距离
```
// 求 el 到文档顶部的距离
let {top}=el.getBoundingClientRect()
let height=window.scrollY+top
```
> top 可能是负值，表示元素在当前文档顶部之上

#### currentTarget 和 target
```
onClick(event){
    console.log(event.currentTarget) // 绑定监听事件的元素
    console.log(event.target) // 触发事件的元素
}
```

#### appendChild 和 cloneNode
* appendChild()
> 如果被插入的节点已经存在于当前文档的文档树中,则那个节点会首先从原先的位置移除,然后再插入到新的位置.
* cloneNode()
```
// 只复制最表层节点，不复制子节点
let copy=el.cloneNode(false)

// 复制以el为根节点的整棵DOM树
let copy=el.cloneNode(true)
```
let table2=this.$refs.table.cloneNode(true)
this.$refs.wrapper.appendChild(table2)

#### 根据a的宽度修改b的宽度
```
let {width}=a.getBoundingClientRect()
b.style.width=`${width}px`
```

#### table 相关
* 获取 table 的 thead 子节点
```
let tableHeader=Array.from(table.children).filter(node=>node.tagName.toLowerCase()==='thead')[0]
```
* 删除 table 的 tbody
```
let tableHeader2
Array.from(table.children).map(node=>{
    if(node.tagName.toLowerCase()!=='thead'){
        node.remove()
    } else{
        tableHeader2=node
    }
})
```
* 为 table 添加class
```
table.classList.add('tableCopy')
```
* 获取 table 的 border-bottom 宽度（style.borderBottom 可写不可读）
```
getComputedStyle(this.table,null).getPropertyValue('border-bottom-width'));
```

#### window 事件
* resize:改变浏览器宽度
* scroll:滚动
    * window.scrollY