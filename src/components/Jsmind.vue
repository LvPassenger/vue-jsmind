<template>
  <div
    class="jsmind"
  >
    <!-- 右上角菜单 -->
    <div class="toolbar">
      <ul class="toolbar-list">
        <li class="item">
          <span
            size="16"
            class="percent"
            style="font-size: 14px; color: rgb(29, 29, 31)"
            @click="zoom.value = 100"
            >{{ zoom.value }}%
          </span>
          <div class="scale-slide">
            <ul>
              <li class="normal-item" title="缩小" @click="zoomOut">
                <svg
                  width="16"
                  height="16"
                  viewBox="0 0 16 16"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path
                    d="M12.98 11.95l2.91 2.9c.15.15.15.38 0 .53l-.51.51a.37.37 0 01-.52 0L11.95 13a7.32 7.32 0 111.03-1.03zm-5.66 1.22a5.85 5.85 0 100-11.7 5.85 5.85 0 000 11.7zM4.76 6.6h5.12c.2 0 .37.16.37.36v.73c0 .2-.17.37-.37.37H4.76a.37.37 0 01-.37-.37v-.73c0-.2.16-.36.37-.36z"
                    fill="#2B2F36"
                    fill-rule="nonzero"
                  ></path>
                </svg>
              </li>

              <li class="slider">
                <el-slider
                  v-model="zoom.value"
                  :show-tooltip="false"
                  :min="zoom.min"
                  :max="zoom.max"
                ></el-slider>
              </li>

              <li class="normal-item" title="画布放大" @click="zoomIn">
                <svg
                  width="16"
                  height="16"
                  viewBox="0 0 16 16"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path
                    d="M12.98 11.95l2.91 2.9c.15.15.15.38 0 .53l-.51.51a.37.37 0 01-.52 0L11.95 13a7.32 7.32 0 111.03-1.03zm-6.4-5.36V4.76c0-.2.17-.37.37-.37h.73c.2 0 .37.16.37.37v1.83h1.83c.2 0 .37.16.37.36v.73c0 .2-.17.37-.37.37H8.05v1.83c0 .2-.16.37-.37.37h-.73a.37.37 0 01-.36-.37V8.05H4.76a.37.37 0 01-.37-.37v-.73c0-.2.16-.36.37-.36h1.83zm.74 6.58a5.85 5.85 0 100-11.7 5.85 5.85 0 000 11.7z"
                    fill="#2B2F36"
                    fill-rule="nonzero"
                  ></path>
                </svg>
              </li>
            </ul>
          </div>
        </li>

        <div class="layout item">
          <svg
            width="24"
            height="24"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M12.56 4.06c1.41 0 2.8.28 4.05.8l-.99 1.21a9.3 9.3 0 00-2.67-.5l-.4-.01h-.43a9.14 9.14 0 00-5.28 2c-.72.61-1.3 1.32-1.69 2.09a5.1 5.1 0 000 4.82c.39.74.95 1.41 1.68 2 .73.59 1.59 1.06 2.55 1.39a9.75 9.75 0 004.5.42l.44-.06.53-.11.06-.02c.07-.03.14-.1.2-.2a.8.8 0 00.1-.47l-.03-.12-.03-.1-.05-.22a3.32 3.32 0 01.46-2.53c.52-.8 1.36-1.3 2.27-1.36H19.45l.1-.01c.48-.07.87-.53.96-1.1l.02-.14v-.25l-.02-.22-.05-.29a5.6 5.6 0 00-1.13-2.4l.96-1.2a7.08 7.08 0 011.63 3.34l.06.34.04.34v.37c-.08 1.45-1.12 2.6-2.4 2.7H18.02c-.48 0-.94.26-1.23.7-.22.34-.32.75-.28 1.16l.02.18.07.27a2.3 2.3 0 01-.2 1.75c-.24.41-.6.72-1 .86l-.17.05-.57.12c-.42.08-.84.13-1.26.16l-.42.03h-.44c-1.26 0-2.5-.2-3.65-.6a9.85 9.85 0 01-3-1.63 7.91 7.91 0 01-2.07-2.47 6.58 6.58 0 010-6.19A8.24 8.24 0 015.9 6.42a9.85 9.85 0 013-1.72c.92-.32 1.86-.53 2.81-.6l.41-.02.43-.01h.02zM7.4 12.4a1.1 1.1 0 110 2.2 1.1 1.1 0 010-2.2zm12.29-9.01a.5.5 0 01.63-.13l.07.05.4.31c.18.16.23.42.12.63l-.05.08-7.69 9.6-1.14.51a.2.2 0 01-.28-.17v-.05L12 13l7.69-9.61zM8.4 8.4a1.1 1.1 0 110 2.2 1.1 1.1 0 010-2.2zm4.2-1.5a1.1 1.1 0 110 2.2 1.1 1.1 0 010-2.2z"
              fill="#2B2F36"
              fill-rule="evenodd"
            ></path>
          </svg>
          <div class="structure">
            <div class="tab-content">
              <h3 class="tab-label">结构</h3>
              <ul class="struct-list">
                <li @click="toggleStucture('side')">
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="32"
                    height="32"
                    viewBox="0 0 32 32"
                  >
                    <g fill="none" fill-rule="evenodd">
                      <path
                        :fill="pathColor('side')"
                        d="M18.77 15.25H22a.75.75 0 110 1.5h-4c1.05.97 1.9 3.27 2.76 7.02.4 1.73.88 2.48 1.24 2.48a.75.75 0 110 1.5c-1.33 0-2.16-1.29-2.7-3.65-.87-3.77-1.76-5.93-2.38-6.32A2 2 0 0116 18c-.35 0-.68-.09-.97-.25H15c-.36 0-.84.75-1.24 2.48-1.07 4.66-2.13 7.1-3.56 7.5a.75.75 0 11-.4-1.45c.62-.18 1.58-2.37 2.5-6.38.34-1.5.8-2.57 1.44-3.15H10a.75.75 0 110-1.5h3.02a9.55 9.55 0 01-.72-2.15c-.92-4.01-1.88-6.2-2.5-6.38a.75.75 0 11.4-1.44c1.43.4 2.5 2.83 3.56 7.49.21.93.45 1.57.68 1.97A2 2 0 0116 14a2 2 0 011.43.6c.55-.95 1.22-2.87 1.87-5.7.54-2.36 1.37-3.65 2.7-3.65a.75.75 0 110 1.5c-.36 0-.84.75-1.24 2.48-.64 2.8-1.28 4.79-2 6.02z"
                      ></path>
                      <rect
                        width="5"
                        height="3"
                        x="26"
                        y="5"
                        :fill="rectColor('side')"
                        rx=".5"
                      ></rect>
                      <rect
                        width="5"
                        height="3"
                        x="26"
                        y="15"
                        :fill="rectColor('side')"
                        rx=".5"
                      ></rect>
                      <rect
                        width="5"
                        height="3"
                        x="26"
                        y="25"
                        :fill="rectColor('side')"
                        rx=".5"
                      ></rect>
                      <rect
                        width="5"
                        height="3"
                        x="1"
                        y="5"
                        :fill="rectColor('side')"
                        rx=".5"
                      ></rect>
                      <rect
                        width="5"
                        height="3"
                        x="1"
                        y="15"
                        :fill="rectColor('side')"
                        rx=".5"
                      ></rect>
                      <rect
                        width="5"
                        height="3"
                        x="1"
                        y="25"
                        :fill="rectColor('side')"
                        rx=".5"
                      ></rect>
                    </g>
                  </svg>
                </li>

                <li class="" @click="toggleStucture('right')">
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="32"
                    height="32"
                    viewBox="0 0 32 32"
                  >
                    <g
                      fill="none"
                      fill-rule="evenodd"
                      transform="translate(2 4)"
                    >
                      <path
                        :fill="pathColor('right')"
                        d="M4.92 11.25H9.5a.75.75 0 110 1.5H4.92c.87 1.34 1.66 3.56 2.44 6.7.5 1.94 1.1 2.8 1.64 2.8a.75.75 0 110 1.5c-1.48 0-2.45-1.39-3.1-3.94-.82-3.33-1.67-5.5-2.4-6.5a2 2 0 110-2.63c.73-.98 1.58-3.16 2.4-6.49C6.56 1.64 7.53.25 9 .25a.75.75 0 010 1.5c-.55 0-1.15.86-1.64 2.8-.78 3.14-1.57 5.36-2.44 6.7z"
                      ></path>
                      <rect
                        width="12"
                        height="3"
                        x="14"
                        :fill="rectColor('right')"
                        rx=".5"
                      ></rect>
                      <rect
                        width="12"
                        height="3"
                        x="14"
                        y="10.5"
                        :fill="rectColor('right')"
                        rx=".5"
                      ></rect>
                      <rect
                        width="12"
                        height="3"
                        x="14"
                        y="21"
                        :fill="rectColor('right')"
                        rx=".5"
                      ></rect>
                    </g>
                  </svg>
                </li>
                <li class="" @click="toggleStucture('left')">
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="32"
                    height="32"
                    viewBox="0 0 32 32"
                  >
                    <g
                      fill="none"
                      fill-rule="evenodd"
                      transform="matrix(-1 0 0 1 29 4)"
                    >
                      <path
                        :fill="pathColor('left')"
                        d="M4.92 11.25H9.5a.75.75 0 110 1.5H4.92c.87 1.34 1.66 3.56 2.44 6.7.5 1.94 1.1 2.8 1.64 2.8a.75.75 0 110 1.5c-1.48 0-2.45-1.39-3.1-3.94-.82-3.33-1.67-5.5-2.4-6.5a2 2 0 110-2.63c.73-.98 1.58-3.16 2.4-6.49C6.56 1.64 7.53.25 9 .25a.75.75 0 010 1.5c-.55 0-1.15.86-1.64 2.8-.78 3.14-1.57 5.36-2.44 6.7z"
                      ></path>
                      <rect
                        width="12"
                        height="3"
                        x="14"
                        :fill="rectColor('left')"
                        rx=".5"
                      ></rect>
                      <rect
                        width="12"
                        height="3"
                        x="14"
                        y="10.5"
                        :fill="rectColor('left')"
                        rx=".5"
                      ></rect>
                      <rect
                        width="12"
                        height="3"
                        x="14"
                        y="21"
                        :fill="rectColor('left')"
                        rx=".5"
                      ></rect>
                    </g>
                  </svg>
                </li>
              </ul>
            </div>
          </div>
        </div>

        <div
          class="reset item normal-item"
          title="定位到中心主题"
          @click="reset"
        >
          <svg
            width="16"
            height="16"
            viewBox="0 0 16 16"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M.77 0h3.46c.21 0 .38.17.38.38v.77c0 .22-.17.39-.38.39h-2.7v2.7c0 .2-.16.38-.38.38H.38A.38.38 0 010 4.23V.77C0 .34.34 0 .77 0zm14.45 16h-3.46a.38.38 0 01-.38-.39v-.76c0-.22.17-.39.38-.39h2.7v-2.7c0-.2.17-.38.38-.38h.77c.21 0 .38.18.38.39v3.46c0 .43-.34.77-.77.77zM0 15.23v-3.46c0-.21.17-.39.38-.39h.77c.22 0 .39.18.39.39v2.7h2.69c.21 0 .38.16.38.38v.77c0 .2-.17.38-.38.38H.77a.77.77 0 01-.77-.77zM16 .78v3.46c0 .21-.17.38-.38.38h-.77a.38.38 0 01-.39-.38v-2.7h-2.69a.38.38 0 01-.38-.38V.4c0-.2.17-.38.38-.38h3.46c.43 0 .77.34.77.77zm-8 9.99a2.77 2.77 0 110-5.54 2.77 2.77 0 010 5.54z"
              fill="#2B2F36"
              fill-rule="nonzero"
            ></path>
          </svg>
        </div>
      </ul>
    </div>

    <div class="top-bar">
      <ul class="filter">
        <li
          :class="[item.type, item.status && 'active']"
          @click="toggleFilter(item)"
          v-for="item in filterTypes"
          :key="item.value"
        >
          <i></i>
          <span>{{ item.name }}</span>
        </li>
      </ul>

      <span class="export" @click="screen_shot">导出图片</span>
    </div>

    <div class="jsmind_layout">
      <div
        id="jsmind_container"
        ref="container"
        @click="nodeClick"
        @contextmenu.prevent.stop="nodeClick"
      ></div>

      <el-dialog
        :title="createType === 'bro' ? '插入平级' : '插入子级'"
        :visible.sync="dialogVisible"
        width="600px"
        @closed="form = {}"
        :destroy-on-close="true"
        :lock-scroll="false"
        :append-to-body="true"
        v-if="selectNodeInfo"
      >
        <el-form label-width="80px" class="form-con">
          <el-form-item label="卡片标题">
            <el-input
              type="textarea"
              :rows="2"
              v-model="selectNodeInfo.Name"
              class="ele-width"
              maxLength="64"
            ></el-input>
          </el-form-item>
        </el-form>
        <template v-slot:footer>
          <div class="right mr-10">
            <el-button
              type="primary"
              class="common-btn"
              @click="sureEditNode"
              size="medium"
              >确 定</el-button
            >
          </div>
        </template>
      </el-dialog>
    </div>

    <!-- 右键菜单 -->
    <el-menu
      class="context-menu"
      v-show="showMenu"
      :style="{
        left: menuStyle.left,
        top: menuStyle.top,
        bottom: menuStyle.bottom,
        right: menuStyle.right
      }"
      ref="context"
    >
      <slot>
        <el-menu-item @click="addBrother">插入平级</el-menu-item>
        <el-menu-item @click="addChild">插入子级</el-menu-item>
        <el-menu-item @click="delCard">删除卡片</el-menu-item>
      </slot>
    </el-menu>
  </div>
</template>

<script>

export default {
  watch: {
    'zoom.value' (val) {
      const zoom = val / 100
      this.jm.view.setZoom(zoom)
    },
    selectTypes (v) {
      this.loopTreeData(this.mind.data.children, (item) => {
        if (v.length) {
          if (v.includes(item.type)) {
            this.jm.set_node_color(item.id, this.bgMap[item.type].original, '#fff')
          } else {
            this.jm.set_node_color(item.id, this.bgMap[item.type].transparent, '#fff')
          }
        } else {
          this.jm.set_node_color(item.id, this.bgMap[item.type].transparent, '#fff')
        }
      })
    }
  },
  computed: {
    pathColor () {
      return function (type) {
        return this.structure.active === type ? this.structure.pathActiveColor : this.structure.pathOrginalColor
      }
    },
    rectColor () {
      return function (type) {
        return this.structure.active === type ? this.structure.rectActiveColor : this.structure.rectOrginalColor
      }
    }
  },
  data () {
    return {
      mind: {
        meta: {
          name: '思维导图',
          author: 'hizzgdev@163.com',
          version: '0.2'
        },
        format: 'node_tree',
        data: {
          id: 'root',
          topic: 'jsMind',
          children: [
            {
              id: 'easy', // [必选] ID, 所有节点的ID不应有重复，否则ID重复的结节将被忽略
              topic: 'Easy', // [必选] 节点上显示的内容
              direction: 'right', // [可选] 节点的方向，此数据仅在第一层节点上有效，目前仅支持 left 和 right 两种，默认为 right
              expanded: true, // [可选] 该节点是否是展开状态，默认为 true
              type: '4', // [可选]自定义节点类型
              children: [
                { id: 'easy1', topic: 'Easy to show', type: '1' },
                { id: 'easy2', topic: 'Easy to edit', type: '2' },
                { id: 'easy3', topic: 'Easy to store', type: '1' },
                { id: 'easy4', topic: 'Easy to embed', type: '3' }
              ]
            },
            {
              id: 'open',
              topic: 'Open Source',
              direction: 'right',
              expanded: true,
              type: '4',
              children: [
                { id: 'open1', topic: 'on GitHub', type: '1' },
                { id: 'open2', topic: 'BSD License', type: '1' }
              ]
            },
            {
              id: 'powerful',
              topic: 'Powerful',
              direction: 'right',
              type: '4',
              children: [
                { id: 'powerful1', topic: 'Base on Javascript', type: '3' },
                { id: 'powerful2', topic: 'Base on HTML5', type: '2' },
                { id: 'powerful3', topic: 'Depends on you', type: '4' }
              ]
            },
            {
              id: 'other',
              topic: 'test node',
              direction: 'right',
              type: '4',
              children: [
                { id: 'other1', topic: "I'm from local variable", type: '1' },
                { id: 'other2', topic: 'I can do everything', type: '4' }
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
        shortcut: { // 禁用快捷键
          enable: false
        }
      },
      zoom: {
        value: 100, // 层级大小
        min: 10, // 最小层级
        max: 400 // 最大层级
      },
      bgMap: {
        1: {
          original: 'rgb(212, 42, 42)',
          transparent: 'rgb(212, 42, 42, 0.2)'
        },
        2: {
          original: 'rgb(100, 201, 53)',
          transparent: 'rgb(100, 201, 53, 0.2)'
        },
        3: {
          original: 'rgb(67, 50, 173)',
          transparent: 'rgb(67, 50, 173, 0.2)'
        },
        4: {
          original: 'rgb(25, 144, 255)',
          transparent: 'rgb(25, 144, 255, 0.2)'
        }
      },
      structure: {
        active: 'right',
        pathOrginalColor: '#2B2F36',
        pathActiveColor: '#3370FF',
        rectOrginalColor: '#C3C6CB',
        rectActiveColor: '#BACEFD'
      },
      dialogVisible: false,
      selectNodeInfo: {
        id: null,
        Name: ''
      }, // 选中节点信息
      tempNodeInfo: null, // 保存修改之前的信息
      createType: '', // 添加平级or子级
      showMenu: false, // 是否显示右键菜单栏
      menuStyle: {
        top: '',
        bottom: '',
        left: '',
        right: ''
      },
      filterTypes: [
        {
          type: 'kd',
          value: '4',
          name: '考点',
          status: true
        },
        {
          type: 'zsd',
          value: '1',
          name: '知识点',
          status: true
        },
        {
          type: 'zskp',
          value: '2',
          name: '知识卡片',
          status: true
        },
        {
          type: 'st',
          value: '3',
          name: '练习题',
          status: true
        }
      ],
      typeQueue: new Set(['1', '2', '3', '4']), // 选中types Set
      selectTypes: ['1', '2', '3', '4'] // 选中types Array
    }
  },
  methods: {
    // 筛选树结构
    toggleFilter (item) {
      item.status = !item.status
      item.status ? this.typeQueue.add(item.value) : this.typeQueue.delete(item.value)
      this.selectTypes = [...this.typeQueue]
    },

    // 重置视图
    reset () {
      document.querySelector('.root').scrollIntoView({
        block: 'center',
        behavior: 'smooth'
      })
    },

    // 缩小
    zoomOut () {
      this.jm.view.zoomOut()
      this.zoom.value = parseInt(this.jm.view.actualZoom * 100)
    },
    // 放大
    zoomIn () {
      this.jm.view.zoomIn()
      this.zoom.value = parseInt(this.jm.view.actualZoom * 100)
    },

    // 循环树结构
    loopTreeData (list, callback) {
      (function doOneFloor (list) {
        if (Array.isArray(list)) {
          for (let i = 0; i < list.length; i++) {
            const item = list[i]
            callback(item, i)
            if (item.children && item.children.length > 0) {
              doOneFloor(item.children)
            }
          }
        }
      })(list)
    },

    // 设置背景颜色
    setColor () {
      this.jm.set_node_color('root', this.bgMap[4].original, '#fff')
      this.loopTreeData(this.mind.data.children, (item) => {
        if (this.selectTypes.length) {
          if (this.selectTypes.includes(item.type)) {
            this.jm.set_node_color(item.id, this.bgMap[item.type].original, '#fff')
          } else {
            this.jm.set_node_color(item.id, this.bgMap[item.type].transparent, '#fff')
          }
        } else {
          this.jm.set_node_color(item.id, this.bgMap[item.type].transparent, '#fff')
        }
      })
    },

    // 切换思维导图结构
    toggleStucture (type) {
      if (this.structure.active === type) return
      this.structure.active = type
      switch (type) {
        case 'side':
          // 两边分布
          this.loopTreeData(this.mind.data.children, (item, i) => { item.direction = i % 2 ? 'left' : 'right' })
          break

        case 'left':
          // 向左分布
          this.loopTreeData(this.mind.data.children, (item) => { item.direction = 'left' })
          break

        case 'right':
          // 向右分布
          this.loopTreeData(this.mind.data.children, (item) => { item.direction = 'right' })
          break

        default:
          break
      }

      this.jm.show(this.mind)
      this.init()
    },

    // 初始化配置
    init () {
      this.jm.view.minZoom = 0.1
      this.jm.view.maxZoom = 5
      this.jm.expand_all()
      this.setColor()

      // 重写编辑完成事件
      this.jm.view.edit_node_end = () => {
        const node = this.jm.view.get_editing_node()
        const viewData = node._data.view
        const element = viewData.element
        element.style.zIndex = 'auto'
        if (node.topic === this.editor.value) {
          this.jm.update_node(node.id, node.topic)
          return
        }
        node.topic = this.editor.value
        if (!node.topic) {
          this.$message.info('请输入卡片标题')
        }
        this.jm.update_node(node.id, node.topic)

        // TODO 调接口
      }

      // 右键菜单
      this.jm.view.add_event(this.editor, 'contextmenu', (e) => {
        const selectedNode = this.jm.get_selected_node()
        if (selectedNode && selectedNode.data.type) {
          e.preventDefault()
          const el = document.querySelector('.context-menu .el-menu-item')
          const width = parseFloat(window.getComputedStyle(el).width)
          const height = parseFloat(window.getComputedStyle(el).height) * 3 + 12
          const windowHeight = window.innerHeight
          const windowWidth = window.innerWidth

          // 极限位置 避免越界
          if (e.clientY + height > windowHeight) {
            this.menuStyle.left = e.clientX + 'px'
            this.menuStyle.top = 'unset'
            this.menuStyle.bottom = 0
          } else if (e.clientX + width > windowWidth) {
            this.menuStyle.top = e.clientY + 'px'
            this.menuStyle.left = 'unset'
            this.menuStyle.right = 0
          } else {
            this.menuStyle.left = e.clientX + 'px'
            this.menuStyle.top = e.clientY + 'px'
            this.menuStyle.bottom = 'unset'
          }
          this.showMenu = true
        } else {
          this.showMenu = false
        }
      })
    },
    // 获取选中标签的 ID
    get_selected_nodeid () {
      const selectedNode = this.jm.get_selected_node()
      if (selectedNode) {
        return selectedNode.id
      } else {
        return null
      }
    },

    // 保存节点
    sureEditNode () {
      if (!this.selectNodeInfo.Name) {
        this.$message.info('请输入卡片标题')
        return
      }

      if (this.createType === 'bro') {
        // 平级
        // TODO 调接口
      } else {
        // 子级
        // TODO 调接口
      }
      this.dialogVisible = false
    },

    // 拖拽
    handleDrop (draggingNode, dropNode) {
      // 前一个兄弟节点
      const prevNode = this.jm.find_node_before(dropNode)
      // 获取移动后的node
      const dragForm = {
        modelId: '',
        treeNum: !prevNode ? draggingNode : prevNode.id,
        thisTreeNum: dropNode
      }
      console.log('dragForm', dragForm)

      // TODO 调接口
    },
    // 单击重置选中背景颜色
    nodeClick () {
      const selectedId = this.get_selected_nodeid()
      if (!selectedId) return
      const nodeObj = this.jm.get_node(selectedId)
      this.jm.set_node_color(selectedId, nodeObj.data['background-color'], '#fff')
    },

    // 插入卡片
    insertNode () {
      const selectedNode = this.jm.get_selected_node()
      if (selectedNode.data) {
        this.$emit('insert', selectedNode.data)
      } else {
        this.$message.error('请选择卡片')
      }
      this.showMenu = false
    },
    // 插入平级
    addBrother () {
      const selectedNode = this.jm.get_selected_node()
      if (selectedNode.data) {
        this.dialogVisible = true
        this.selectNodeInfo = {
          id: selectedNode.data.num,
          Name: ''
        }
        this.createType = 'bro'
      } else {
        this.$message.error('请选择卡片')
      }

      this.showMenu = false
    },

    // 插入子级
    addChild () {
      const selectedNode = this.jm.get_selected_node()
      if (selectedNode.data) {
        this.dialogVisible = true
        this.selectNodeInfo = {
          id: selectedNode.data.num,
          Name: ''
        }
        this.createType = 'child'
      } else {
        this.$message.error('请选择卡片')
      }

      this.showMenu = false
    },

    // 删除卡片
    delCard () {
      const selectedNode = this.jm.get_selected_node()
      if (selectedNode.data) {
        // TODO
        this.jm.remove_node(selectedNode.id)
        // 获取数据
        console.log(this.jm.get_data('node_tree'))
      } else {
        this.$message.error('请选择卡片')
      }
      this.showMenu = false
    },

    // 鼠标滚轮放大缩小
    mouseWheel () {
      if (document.addEventListener) {
        document.addEventListener('domMouseScroll', this.scrollFunc, false)
      }
      this.$refs.container.onmousewheel = this.scrollFunc
    },
    // 滚轮缩放
    scrollFunc (e) {
      e = e || window.event
      if (e.wheelDelta) {
        if (e.wheelDelta > 0) {
          this.zoomIn()
        } else {
          this.zoomOut()
        }
      } else if (e.detail) {
        if (e.detail > 0) {
          this.zoomIn()
        } else {
          this.zoomOut()
        }
      }
      e.preventDefault()
      this.jm.resize()
    },

    // 导出图片
    screen_shot () {
      // 去除透明度
      this.loopTreeData(this.mind.data.children, (item) => this.jm.set_node_color(item.id, this.bgMap[item.type].original, '#fff'))
      try {
        this.jm.screenshot.shootDownload()
      } catch (error) {
        console.log(error)
      }
      setTimeout(() => {
        this.setColor()
      }, 1000)
    },
    // 鼠标拖拽
    mouseDrag () {
      // 里层
      const el = document.querySelector('.jsmind-inner')
      // 选中节点
      let selected

      el.onmousedown = (ev) => {
        // 选中节点
        selected = this.jm.get_selected_node()
        // 标识 是否拖拽节点 避免冲突
        this.dragNodeFlag = !!selected

        const disX = ev.clientX
        const disY = ev.clientY
        const originalScrollLeft = el.scrollLeft
        const originalScrollTop = el.scrollTop
        const originalScrollBehavior = el.style['scroll-behavior']
        const originalPointerEvents = el.style['pointer-events']
        // auto: 默认值，表示滚动框立即滚动到指定位置。
        el.style['scroll-behavior'] = 'auto'
        // 鼠标移动事件是监听的整个document，这样可以使鼠标能够在元素外部移动的时候也能实现拖动
        document.onmousemove = (ev) => {
          if (this.dragNodeFlag) return
          this.drag = false
          ev.preventDefault()
          // 计算拖拽的偏移距离
          const distanceX = ev.clientX - disX
          const distanceY = ev.clientY - disY

          el.scrollTo(originalScrollLeft - distanceX, originalScrollTop - distanceY)

          // 在鼠标拖动的时候将点击事件屏蔽掉
          el.style['pointer-events'] = 'none'
          el.style.cursor = 'grabbing'
        }
        document.onmouseup = () => {
          if (!this.dragNodeFlag) {
            el.style['scroll-behavior'] = originalScrollBehavior
            el.style['pointer-events'] = originalPointerEvents
            el.style.cursor = 'grab'
          }
          document.onmousemove = document.onmouseup = null
        }
      }
    }
  },
  mounted () {
    this.jm = jsMind.show(this.options, this.mind)

    // 自定义拖拽完成事件
    jsMind.draggable.prototype.handleDrag = (srcNode, targetNode, targetDirect) => {
      const nextParentId = srcNode.parent.id
      this.handleDrop(nextParentId, srcNode.id)
    }
    this.editor = this.jm.view.e_editor
    this.init()
    this.mouseWheel()
    this.mouseDrag()
  },
  beforeDestroy () {
    document.removeEventListener('domMouseScroll', this.scrollFunc, false)
  }
}
</script>

<style lang="less">
@import '../assets/css/style.less';
</style>
