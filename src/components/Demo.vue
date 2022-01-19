<template>
  <div id="jsmind_container"></div>
</template>

<script>
export default {
  data () {
    return {
      mind: {
        /* 元数据，定义思维导图的名称、作者、版本等信息 */
        meta: {
          name: '思维导图',
          author: 'hizzgdev@163.com',
          version: '0.2'
        },
        /* 数据格式声明 */
        format: 'node_tree',
        /* 数据内容 */
        data: {
          id: 'root',
          topic: 'jsMind',
          children: [
            {
              id: 'easy', // [必选] ID, 所有节点的ID不应有重复，否则ID重复的结节将被忽略
              topic: 'Easy', // [必选] 节点上显示的内容
              direction: 'right', // [可选] 节点的方向，此数据仅在第一层节点上有效，目前仅支持 left 和 right 两种，默认为 right
              expanded: true, // [可选] 该节点是否是展开状态，默认为 true
              children: [
                { id: 'easy1', topic: 'Easy to show' },
                { id: 'easy2', topic: 'Easy to edit' },
                { id: 'easy3', topic: 'Easy to store' },
                { id: 'easy4', topic: 'Easy to embed' }
              ]
            },
            {
              id: 'open',
              topic: 'Open Source',
              direction: 'right',
              expanded: true,
              children: [
                { id: 'open1', topic: 'on GitHub' },
                { id: 'open2', topic: 'BSD License' }
              ]
            },
            {
              id: 'powerful',
              topic: 'Powerful',
              direction: 'right',
              children: [
                { id: 'powerful1', topic: 'Base on Javascript' },
                { id: 'powerful2', topic: 'Base on HTML5' },
                { id: 'powerful3', topic: 'Depends on you' }
              ]
            },
            {
              id: 'other',
              topic: 'test node',
              direction: 'right',
              children: [
                { id: 'other1', topic: "I'm from local variable" },
                { id: 'other2', topic: 'I can do everything' }
              ]
            }
          ]
        }
      },
      options: {
        container: 'jsmind_container', // [必选] 容器的ID
        editable: true, // [可选] 是否启用编辑
        theme: '', // [可选] 主题
        view: {
          engine: 'canvas', // 思维导图各节点之间线条的绘制引擎
          hmargin: 120, // 思维导图距容器外框的最小水平距离
          vmargin: 50, // 思维导图距容器外框的最小垂直距离
          line_width: 2, // 思维导图线条的粗细
          line_color: '#ddd' // 思维导图线条的颜色
        },
        layout: {
          hspace: 100, // 节点之间的水平间距
          vspace: 20, // 节点之间的垂直间距
          pspace: 20 // 节点与连接线之间的水平间距（用于容纳节点收缩/展开控制器）
        },
        shortcut: {
          enable: false // 是否启用快捷键 默认为true
        }
      }
    }
  },
  mounted () {
    // 初始化
    this.jm = jsMind.show(this.options, this.mind)
  }
}
</script>

<style lang="less" scoped>
#jsmind_container {
  width: 100%;
  height: 100vh;
}
</style>
