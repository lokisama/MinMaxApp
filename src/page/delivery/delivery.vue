<template>
    <div class="confirmOrderContainer">
        <section v-if="!showLoading">

            <section class="delivery_model container_style">
                <!-- <section class="deliver_time" v-if="false">
                    <p>线路</p>
                    <p>目的地 - 麦当劳</p>
                    <p>漕宝路683号国际商务中心1楼</p>
                </section> -->
                <section class="deliver_time" v-if="true">
                    <p>{{status}}</p>
                </section>
            </section>
            
            <section class="food_list">
              <div id="amap-main"></div>
              <div>
                <!-- <input type="button" class="button" value="开始"  style="position:absolute;top:10px;right:200px"/> -->
                <!-- <input type="button" class="button" value="释放" id="pause" style="position:absolute;top:10px;right:150px"/> -->
                <!-- <input type="button" class="button" value="回收" id="resume" style="position:absolute;top:10px;right:100px"/> -->
                <!-- <input type="button" class="button" value="停止" id="stop" style="position:absolute;top:10px;right:50px"/>
                <input type="button" class="button" value="继续" id="load" style="position:absolute;top:10px;right:0px"/> -->
              </div>
            </section>

            <div class="button_bottom" >

              <div class="button_blue" id="start" v-if="step==0" @click="goToMap(map,data,0,0)">开始导航</div>

              <div id="robot" v-if="step==1">
                <div class="boton_blue robot">
                  <span class="botton_left">1号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,1,0)">取&nbsp;&nbsp;餐</span>
                </div>
                <div class="boton_blue robot">
                  <span class="botton_left">2号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,1,1)">取&nbsp;&nbsp;餐</span>
                </div>
              </div>

              <div class="button_blue" id="resume" v-if="step==2" @click="goToMap(map,data,2,0)">点击继续导航</div>

              <div id="toCus" v-if="step==3">
                <div class="boton_blue robot">
                  <span class="botton_left">1号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,3,0)">送&nbsp;&nbsp;餐</span>
                </div>
                <div class="boton_blue robot">
                  <span class="botton_left">2号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,3,1)">送&nbsp;&nbsp;餐</span>
                </div>
                <div class="boton_blue robot">
                  <span class="botton_left">2号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,3,2)">送&nbsp;&nbsp;餐</span>
                </div>
              </div>

              <div class="button_blue" id="resume" v-if="step==4" @click="goToMap(map,data,4,0)">点击继续导航</div>

              <div id="robot" v-if="step==5">
                <div class="boton_blue robot">
                  <span class="botton_left">1号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,5,0)">送&nbsp;&nbsp;餐</span>
                </div>
                <div class="boton_blue robot">
                  <span class="botton_left">2号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,5,1)">送&nbsp;&nbsp;餐</span>
                </div>
              </div>

              <div class="button_blue" id="resume" v-if="step==6" @click="goToMap(map,data,6,0)">点击继续导航</div>

              <div id="robot" v-if="step==7">
                <div class="boton_blue robot">
                  <span class="botton_left">1号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,7,0)">取&nbsp;&nbsp;餐</span>
                </div>
              </div>


              <div class="button_blue" id="resume" v-if="step==8" @click="goToMap(map,data,8,0)">点击继续导航</div>

              <div id="robot" v-if="step==9">
                <div class="boton_blue robot">
                  <span class="botton_left">1号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,9,0)">送&nbsp;&nbsp;餐</span>
                </div>
                <div class="boton_blue robot">
                  <span class="botton_left">2号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,9,1)">送&nbsp;&nbsp;餐</span>
                </div>
                <div class="boton_blue robot">
                  <span class="botton_left">3号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,9,2)">送&nbsp;&nbsp;餐</span>
                </div>
              </div>
              <div class="button_blue" id="resume" v-if="step==10" @click="goToMap(map,data,10,0)">点击继续导航</div>

              <div id="robot" v-if="step==11">
                <div class="boton_blue robot">
                  <span class="botton_left">1号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,11,0)">送&nbsp;&nbsp;餐</span>
                </div>
                <div class="boton_blue robot">
                  <span class="botton_left">2号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,11,1)">送&nbsp;&nbsp;餐</span>
                </div>
              </div>

              <div class="button_blue" id="resume" v-if="step==12" @click="goToMap(map,data,12,0)">点击继续导航</div>

              <div id="robot" v-if="step==13">
                <div class="boton_blue robot">
                  <span class="botton_left">1号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,13,0)">送&nbsp;&nbsp;餐</span>
                </div>
                <div class="boton_blue robot">
                  <span class="botton_left">2号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,13,1)">送&nbsp;&nbsp;餐</span>
                </div>
                <div class="boton_blue robot">
                  <span class="botton_left">3号机器人</span>
                  <span class="botton_right waitforStore" @click="goToMap(map,data,13,1)">送&nbsp;&nbsp;餐</span>
                </div>
              </div>
            </div>
            <foot-guide></foot-guide>
            
            <transition name="fade">
                
            </transition>
            <transition name="slid_up">
               
            </transition>
        </section>
        <loading v-if="showLoading"></loading>
        <alert-tip v-if="showAlert" @closeTip="showAlert = false" :alertText="alertText"></alert-tip>
        <transition name="router-slid" mode="out-in">
            <router-view></router-view>
        </transition>
    </div>
</template>

<script>
    import {mapState, mapMutations} from 'vuex'
    import headTop from 'src/components/header/head'
    import alertTip from 'src/components/common/alertTip'
    import loading from 'src/components/common/loading'
    import {checkout, getAddress, placeOrders, getAddressList, offerToQueue, putToMap, getFromMap} from 'src/service/getData'
    import footGuide from '../../components/footer/footGuideD'
    import { lazyAMapApiLoaderInstance } from 'vue-amap';
    export default {
        data(){
            return {
                status:'等待指令',
                rbtReady:0,
                map: null,
                car: null,
                step: 0,
                robot:[],
                userStatus:null,
                geohash: '', //geohash位置信息
                shopId: null, //商店id值
                showLoading: true, //显示加载动画
                checkoutData: null,//数据返回值
                shopCart: null,//购物车数据
                showPayWay: false,//显示付款方式
                payWayId: 1, //付款方式
                showAlert: false, //弹出框
                alertText: null, //弹出框内容
                data: [
  {
    "id":0,
    "step": 0,
    "type": 2,
    "total": 1,
    "status":"正在前往目的地",
    "path": [
      {
        "status":0,
        "line":[[121.468812, 31.214569], [121.468882, 31.214489], [121.468629, 31.21441]]
      }
    ],
    "point":[
      {
        "type": "customer",
        "location": [121.467423, 31.214727],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.467144, 31.214727],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.467294, 31.214525],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "store",
        "location": [121.468321, 31.214592],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/pic_bsk.png"
      },
      {
        "type": "store",
        "location": [121.467849, 31.213968],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/pic_mdl.png"
      },
      {
        "type": "boton",
        "location": [121.468629, 31.21441],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd.png"
      }
    ]
  },
  {
    "id":1,
    "step": 1,
    "type": 1,
    "total": 2,
    "status":"机器人已激活",
    "path": [
      {
        "status": 0,
        "line":[[121.468629, 31.21441], [121.468321, 31.214592], [121.468629, 31.21441]]
      },
      {
        "status": 0,
        "line": [[121.468629, 31.21441], [121.467849, 31.213968], [121.468629, 31.21441]]
      }
    ],
    "point":[
      {
        "type": "customer",
        "location": [121.467423, 31.214727],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.467144, 31.214727],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.467294, 31.214525],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "store",
        "location": [121.468321, 31.214592],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/pic_bsk.png"
      },
      {
        "type": "store",
        "location": [121.467849, 31.213968],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/pic_mdl.png"
      },
      {
        "type": "boton",
        "location": [121.468629, 31.21441],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd.png"
      }
    ]

  },
  {
    "id":2,
    "step": 2,
    "type": 2,
    "total": 1,
    "status":"正在前往目的地",
    "path":[
      {
        "status": 0,
        "line": [[121.468629, 31.21441], [121.468174, 31.214268], [121.467859, 31.21479]]
      }
    ],
    "point":[
      {
        "type": "customer",
        "location": [121.467423, 31.214727],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.467144, 31.214727],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.467294, 31.214525],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.467859, 31.21479],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd.png"
      }
    ]
  },
  {
    "id":3,
    "step": 3,
    "type": 1,
    "total": 3,
    "status":"机器人已激活",
    "path": [
      {
        "status": 0,
        "line":[[121.467859, 31.21479], [121.467423, 31.214727], [121.467859, 31.21479]]
      },
      {
        "status": 0,
        "line": [[121.467859, 31.21479], [121.467144, 31.214727], [121.467859, 31.21479]]
      },
      {
        "status": 0,
        "line": [[121.467859, 31.21479], [121.467294, 31.214525], [121.467859, 31.21479]]
      }
    ],
    "point":[
      {
        "type": "customer",
        "location": [121.467423, 31.214727],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.467144, 31.214727],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.467294, 31.214525],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.467859, 31.21479],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd.png"
      }
    ]
  },
  {
    "id":4,
    "step": 4,
    "type": 2,
    "total": 1,
    "status":"正在前往目的地",
    "path":[
      {
        "status": 0,
        "line": [[121.467859, 31.21479], [121.4676, 31.215218],[121.467433, 31.215594]]
      }
    ],
    "point":[
      {
        "type": "customer",
        "location": [121.467922, 31.215819],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.467686, 31.215856],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.467433, 31.215594],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd.png"
      }
    ]
  },
  {
    "id": 5,
    "step": 5,
    "type": 1,
    "total": 2,
    "status":"机器人已激活",
    "path":[
      {
        "status": 0,
        "line": [[121.467433, 31.215594], [121.467922, 31.215819],[121.467433, 31.215594]]
      },
      {
        "status": 0,
        "line": [[121.467433, 31.215594], [121.467686, 31.215856],[121.467433, 31.215594]]
      }
    ],
    "point":[
      {
        "type": "customer",
        "location": [121.467922, 31.215819],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.467686, 31.215856],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.467433, 31.215594],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd.png"
      }
    ]
  },
  {
    "id": 6,
    "step": 6,
    "type": 2,
    "total": 2,
    "status":"正在前往目的地",
    "path":[
      {
        "status": 0,
        "line": [[121.467433, 31.215594], [121.467213, 31.21609]]
      }
    ],
    "point":[
      {
        "type": "store",
        "location": [121.468193, 31.216344],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/pic_mdl.png"
      },
      {
        "type": "store",
        "location": [121.467796, 31.216271],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/pic_xysj.png"
      },
      {
        "type": "store",
        "location": [121.467433, 31.215594],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd.png"
      },
      {
        "type": "store",
        "location": [121.467213, 31.21609],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd.png"
      }
    ]
  },
  {
    "id": 7,
    "step": 7,
    "type": 1,
    "total": 1,
    "status":"机器人已激活",
    "path":[
      {
        "status": 0,
        "line": [[121.467213, 31.21609], [121.468193, 31.216344],[121.467796, 31.216271],[121.467213, 31.21609]]
      }
    ],
    "point":[
      {
        "type": "store",
        "location": [121.468193, 31.216344],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/pic_mdl.png"
      },
      {
        "type": "store",
        "location": [121.467796, 31.216271],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/pic_xysj.png"
      },
      {
        "type": "store",
        "location": [121.467433, 31.215594],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd.png"
      },
      {
        "type": "store",
        "location": [121.467213, 31.21609],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd.png"
      }
    ]
  },
  {
    "id": 8,
    "step": 8,
    "type": 2,
    "total": 1,
    "status":"正在前往目的地",
    "path":[
      {
        "status": 0,
        "line": [[121.467213, 31.21609], [121.466189, 31.215867]]
      }
    ],
    "point":[
      {
        "type": "customer",
        "location": [121.465867, 31.216324],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.466017, 31.216195],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.466211, 31.216512],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.466189, 31.215867],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd.png"
      }
    ]
  },
  {
    "id": 9,
    "step": 9,
    "type": 1,
    "total": 3,
    "status":"机器人已激活",
    "path":[
      {
        "status": 0,
        "line": [[121.466189, 31.215867], [121.465867, 31.216324],[121.466189, 31.215867]]
      },
      {
        "status": 0,
        "line": [[121.466189, 31.215867], [121.466017, 31.216195],[121.466189, 31.215867]]
      },
      
      {
        "status": 0,
        "line": [[121.466189, 31.215867], [121.466211, 31.216512],[121.466189, 31.215867]]
      }
    ],
    "point":[
      {
        "type": "customer",
        "location": [121.465867, 31.216324],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.466017, 31.216195],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.466211, 31.216512],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.466189, 31.215867],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd.png"
      }
    ]
  },
  {
    "id": 10,
    "step": 10,
    "type": 2,
    "total": 1,
    "status":"正在前往目的地",
    "path":[
      {
        "status": 0,
        "line": [[121.466189, 31.215867], [121.464821, 31.215535], [121.46464, 31.216264]]
      },
    ],
    "point":[
      {
        "type": "customer",
        "location": [121.46432, 31.215876],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.463677, 31.215802],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.46464, 31.216264],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd.png"
      }
    ]
  },
  {
    "id": 11,
    "step": 11,
    "type": 1,
    "total": 2,
    "status":"机器人已激活",
    "path":[
      {
        "status": 0,
        "line": [[121.46464, 31.216264], [121.46432, 31.215876], [121.46464, 31.216264]]
      },
      {
        "status": 0,
        "line": [[121.46464, 31.216264], [121.463677, 31.215802], [121.46464, 31.216264]]
      },
    ],
    "point":[
      {
        "type": "customer",
        "location": [121.46432, 31.215876],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.463677, 31.215802],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      }
    ]
  },
  {
    "id": 12,
    "step": 12,
    "type": 2,
    "total": 1,
    "status":"正在前往目的地",
    "path":[
      {
        "status": 0,
        "line": [[121.46464, 31.216264], [121.46458, 31.216507],[121.465827, 31.216904]]
      },
    ],
    "point":[
      {
        "type": "customer",
        "location": [121.465411, 31.217507],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.465304, 31.2172],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.465819, 31.217466],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.46464, 31.216264],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd.png"
      },
      {
        "type": "customer",
        "location": [121.465827, 31.216904],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd.png"
      }
    ]
  },
  {
    "id": 13,
    "step": 13,
    "type": 1,
    "total": 2,
    "status":"机器人已激活",
    "path":[
      {
        "status": 0,
        "line": [[121.465827, 31.216904], [121.465411, 31.217507], [121.465827, 31.216904]]
      },
      {
        "status": 0,
        "line": [[121.465827, 31.216904], [121.465304, 31.2172], [121.465827, 31.216904]]
      },
      {
        "status": 0,
        "line": [[121.465827, 31.216904], [121.465819, 31.217466], [121.465827, 31.216904]]
      }
    ],
    "point":[
      {
        "type": "customer",
        "location": [121.465411, 31.217507],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.465304, 31.2172],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      },
      {
        "type": "customer",
        "location": [121.465819, 31.217466],
        "pic": "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_yellow.png"
      }
    ]
  }
]
            }
        },
        created(){
            // //获取上个页面传递过来的geohash值
            // this.geohash = this.$route.query.geohash;
            // //获取上个页面传递过来的shopid值
            // this.shopId = this.$route.query.shopId;
            // this.INIT_BUYCART();
            // this.SAVE_SHOPID(this.shopId);
            // //获取当前商铺购物车信息
            // this.shopCart = this.cartList[this.shopId];
        },
        mounted(){
            // runMap();
            this.init();
            this.showLoading = false;

            lazyAMapApiLoaderInstance.load().then(() => {

              this.map = new AMap.Map('amap-main', {
                zoom: 19,
                zoomEnable: true,
                center: [121.468812, 31.214569]
              });

              // _this.goToMap(this.map,this.data,this.step,1);

            });
            
        },
        components: {
            headTop,
            footGuide,
            loading,
        },
        computed: {
            ...mapState([
                'cartList', 'remarkText', 'inputText', 'invoice', 'choosedAddress', 'userInfo'
            ]),
            //备注页返回的信息进行处理
            remarklist: function (){
                let str = new String;
                if (this.remarkText) {
                    Object.values(this.remarkText).forEach(item => {
                        str += item[1] + '，';
                    })
                }
                //是否有自定义备注，分开处理
                if (this.inputText) {
                    return str + this.inputText;
                }else{
                    return str.substr(0, str.lastIndexOf('，')) ;
                }
            },
        },
        methods: {
            ...mapMutations([
                'INIT_BUYCART', 'SAVE_GEOHASH', 'CHOOSE_ADDRESS', 'NEED_VALIDATION', 'SAVE_CART_ID_SIG', 'SAVE_ORDER_PARAM', 'ORDER_SUCCESS', 'SAVE_SHOPID'
            ]),

            init(){
              var _this = this;
              setInterval(() => {
                  getFromMap('MinMaxDeliveryStatus','user').then( res => {
                    var json = JSON.parse(res.data);
                    console.log(json.status);

                    if(json.status === 'start'){

                      // lat===31.214727 && lng ===
                      var iconStore = new AMap.Icon({
                        image: "http://opub24jup.bkt.clouddn.com/coos/boton_dwd_red.png",
                        size: new AMap.Size(18, 18),
                        imageSize: new AMap.Size(18, 18)
                      });
                      _this.userStatus = new AMap.Marker({
                        map: _this.map,
                        position: [121.467423, 31.214727],
                        icon: iconStore,
                        offset: new AMap.Pixel(-9, -9),
                        zIndex: 100
                      });
                    } else if (json.status === 'finish') {
                      if( _this.userStatus != null){
                        _this.map.remove( _this.userStatus);
                      }
                    }
                  })
              },2000)
            },

            goToMap(o,data,step,line){

              offerToQueue('MinMaxStep', '_this.goToMap(_this.map,_this.data,'+ step +',' + line + ');');

              var _this = this;
              if(_this.car == null){
                // 车
                var iconCar = new AMap.Icon({
                  image: 'http://opub24jup.bkt.clouddn.com/ico_car_1.png',
                  size: new AMap.Size(39.5, 28.5),
                  imageSize: new AMap.Size(39.5, 28.5)
                });
                _this.car = new AMap.Marker({
                  map: o,
                  position: data[step].path[0].line[0],
                  icon: iconCar,
                  offset: new AMap.Pixel(-18, -14),
                  autoRotation: true,
                  zIndex: 100
                });
              }

              _this.status = data[step].status;

              // 商家
              if(data[step].point != undefined){
                data[step].point.forEach(point=>{
                  var iconStore = new AMap.Icon({
                    image: point.pic,
                    size: new AMap.Size(18, 18),
                    imageSize: new AMap.Size(18, 18)
                  });
                  var markStore = new AMap.Marker({
                    map: o,
                    position: point.location,
                    icon: iconStore,
                    offset: new AMap.Pixel(-9, -9),
                    zIndex: 100
                  });
                })
              }

              if(data[step].type == 2){
                o.setFitView();
                _this.robot.forEach(rbt=>{
                  o.remove(rbt);
                })
                this.rbtReady = 0;
                // 路线
                var polyline = new AMap.Polyline({
                  map: o,
                  path: data[step].path[0].line,
                  strokeColor: "#FFB63E",
                  strokeOpacity: 1,
                  strokeWeight: 4,
                  strokeStyle: "solid"
                });
                var passedPolyline = new AMap.Polyline({
                  map: o,
                  strokeColor: "#0E92FF",
                  strokeOpacity: 1,
                  strokeWeight: 4,
                  strokeStyle: "solid"
                });
                
                _this.car.moveAlong(data[step].path[0].line, 80);
                _this.car.on('movealong', function(e) {
                  _this.status = "已到达目的地";
                  _this.step = step + 1;
                })

              }else if(data[step].type == 1){

                o.setFitView();
                let rbtNo = line || 0;
                document.querySelectorAll('.botton_right')[rbtNo].style.backgroundColor  = '#C0CCE1';
                document.querySelectorAll('.botton_right')[rbtNo].innerHTML = '等待中';
                data[step].path[rbtNo].status = 1;

                let rbt = new AMap.Marker({
                  map: o,
                  position: data[step].path[rbtNo].line[0],
                  icon: "http://opub24jup.bkt.clouddn.com/coos/ico_robot_small.png",
                  offset: new AMap.Pixel(-28, -28),
                  autoRotation: false
                });

                var polylineRbt = new AMap.Polyline({
                  map: o,
                  path: data[step].path[rbtNo].line,
                  strokeColor: "#677C96",
                  strokeOpacity: 1,
                  strokeWeight: 4,
                  strokeStyle: "dashed"
                });
                // var passedPolylineRbt = new AMap.Polyline({
                //   map: o,
                //   strokeColor: "#677C96",
                //   strokeOpacity: 0,
                //   strokeWeight: 4,
                //   strokeStyle: "dashed"
                // });
                rbt.on('movealong', function(e) {

                  document.querySelectorAll('.botton_right')[rbtNo].style.backgroundColor  = '#16D6B4';
                  document.querySelectorAll('.botton_right')[rbtNo].innerHTML = '已返回';

                  data[step].path[rbtNo].status = 2;
                  _this.rbtReady ++;

                  var lat = rbt.getPosition().lat;
                  var lng = rbt.getPosition().lng;
                  
                  if( _this.rbtReady == data[step].path.length){
                    _this.step = step+1;
                  }

                });
                rbt.on('moveend',function(e){
                  var lat = rbt.getPosition().lat;
                  var lng = rbt.getPosition().lng;
                  if( lat===31.214727 && lng ===121.467423){
                    putToMap('MinMaxDeliveryStatus','user',{ "status" : "finish" });
                  }
                });
                rbt.moveAlong(data[step].path[rbtNo].line, 80);
                _this.robot.push(rbt);
              }
            },

            //初始化数据
            async initData(){
                let newArr = new Array;
                Object.values(this.shopCart).forEach(categoryItem => {
                    Object.values(categoryItem).forEach(itemValue=> {
                        Object.values(itemValue).forEach(item => {
                            newArr.push({
                                attrs: [],
                                extra: {},
                                id: item.id,
                                name: item.name,
                                packing_fee: item.packing_fee,
                                price: item.price,
                                quantity: item.num,
                                sku_id: item.sku_id,
                                specs: [item.specs],
                                stock: item.stock,
                            })
                        })
                    })
                })
                //检验订单是否满足条件
                this.checkoutData = await checkout(this.geohash, [newArr], this.shopId);
                this.SAVE_CART_ID_SIG({cart_id: this.checkoutData.cart.id, sig:  this.checkoutData.sig})
                this.initAddress();
                this.showLoading = false;
            },
            //获取地址信息，第一个地址为默认选择地址
            async initAddress(){
                if (this.userInfo && this.userInfo.user_id) {
                    const addressRes = await getAddressList(this.userInfo.user_id);
                    if (addressRes instanceof Array && addressRes.length) {
                        this.CHOOSE_ADDRESS({address: addressRes[0], index: 0});
                    }
                }
            },
            //显示付款方式
            showPayWayFun(){
                this.showPayWay = !this.showPayWay;
            },
            //选择付款方式
            choosePayWay(is_online_payment, id){
                if (is_online_payment) {
                    this.showPayWay = !this.showPayWay;
                    this.payWayId = id;
                }
            },
            //地址备注颜色
            iconColor(name){
                switch(name){
                    case '公司': return '#4cd964';
                    case '学校': return '#3190e8';
                }
            },
            //确认订单
            async confrimOrder(){
                //用户未登录时弹出提示框
                return;
                
                if (!(this.userInfo && this.userInfo.user_id)) {
                    this.showAlert = true;
                    this.alertText = '请登录';
                    return
                    //未选择地址则提示
                }else if(!this.choosedAddress){
                    this.showAlert = true;
                    this.alertText = '请添加一个收获地址';
                    return
                }
                //保存订单
                this.SAVE_ORDER_PARAM({
                    user_id: this.userInfo.user_id,
                    cart_id: this.checkoutData.cart.id,
                    address_id: this.choosedAddress.id,
                    description: this.remarklist,
                    entities: this.checkoutData.cart.groups,
                    geohash: this.geohash,
                    sig: this.checkoutData.sig,
                });
                //发送订单信息
                let orderRes = await placeOrders(this.userInfo.user_id, this.checkoutData.cart.id, this.choosedAddress.id, this.remarklist, this.checkoutData.cart.groups, this.geohash, this.checkoutData.sig);
                //第一次下单的手机号需要进行验证，否则直接下单成功
                if (orderRes.need_validation) {
                    this.NEED_VALIDATION(orderRes);
                    this.$router.push('/confirmOrder/userValidation');
                }else{
                    this.ORDER_SUCCESS(orderRes);
                    this.$router.push('/confirmOrder/payment');
                }
            },
        },
        watch: {
            userInfo: function (value) {
                if (value && value.user_id) {
                    this.initAddress();
                }
            },
        }
    }

</script>

<style lang="scss" scoped>
    @import 'src/style/mixin';
    .button_bottom{
      position: absolute;
      bottom: 50px;
      left:0;
      right:0;
      .hide{
        display: none!important;
      }
      .button_blue{
        margin:1rem;
        background: #3D83FF;
        text-align: center;
        @include sc(.7rem, #fff);
        padding:.6rem;
        border-radius: 2rem;
      }
      .boton_blue{
        margin:1rem;
        background: #3D83FF;
        text-align: center;
        @include sc(.7rem, #fff);
        border-radius: .2rem;
        display: flex;
        .botton_left{
          border-radius: .2rem;
          border-top-right-radius: 0;
          border-bottom-right-radius: 0;
          @include sc(.7rem, #797B91);
          background-color: #F5F8FF;
          padding:.6rem 1rem;
          flex:1;
        }
        .botton_right{
          width:30%;
          padding:.6rem 1rem;
          &.disable{
            background-color: #C0CCE1;
          }
        }
      }
    }
    
    .confirmOrderContainer{
        background:#fff;
        position:absolute;
        top:0;
        bottom:0;
        left:0;
        right:0;
        overflow: auto;
        p, span{
            font-family: Helvetica Neue,Tahoma,Arial;
        }
    }
    .container_style{
        padding: 0 .7rem;
    }
    .address_container{
        @include fj;
        margin:0 5%;
        margin-top:-1rem;
        margin-bottom:.4rem;
        width:90%;
        min-height: 3.5rem;
        padding: 0 0.6rem;
        background-color: #fff;
        box-shadow: 0px 4px 15px #f7f7f7;
        align-items: center;
        justify-content: center;
        -webkit-box-align: center;
        .address_empty_left{
            display: flex;
            align-items: center;
            line-height: 1.2rem;
            flex:1;
            .location_icon{
                @include wh(.8rem, .8rem);
                fill: $blue;
                margin-right: .2rem;
            }
            .add_address{
                @include sc(.7rem, #333);
            }
            .address_detail_container{
                margin-left: .2rem;
                margin-top: .4rem;
                margin-bottom: .4rem;
                header{
                    span:nth-of-type(1){
                        @include sc(.6rem, #9b9ba8);
                        /*font-size: .8rem;*/
                        font-weight: bold;
                    }
                }
                .address_detail{
                    width: 100%;
                    display: flex;
                    align-items: center;
                    span{
                        @include sc(.5rem, #fff);
                        border-radius: .15rem;
                        background-color: #ff5722;
                        height: .6rem;
                        line-height: .6rem;
                        padding: 0 .2rem;
                        margin-right: .3rem;
                    }
                    p{
                        @include sc(.55rem, #777);
                    }
                }
            }
        }
    }
    .address_empty_right{
        @include wh(.6rem, .6rem);
        fill: #999;
    }
    .delivery_model{
        height: 7.5rem;
        padding-top: 1.95rem;
        padding-bottom: 1rem;
        background:#494e5b;
        @include fj;
        align-items: flex-start;
        justify-content: start;
        -webkit-box-align: flex-start;
        .deliver_text{
            @include sc(.8rem, #333);
            font-weight: bold;
            padding-left: .3rem;
            img{
                @include wh(2.4rem, 2.4rem);
            }
        }
        .deliver_time{
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            margin-left: 1rem;
            p{
               @include sc(.6rem, #9699a9); 
               line-height: 1.2rem;
            }
            p:nth-of-type(1){
                @include sc(1rem, #fff);
                line-height: 1.6rem;
                
                margin-top: .2rem;
                text-align: left;
                border-radius: 0.12rem;
                padding: .1rem;
            }
        }
    }
    .pay_way{
        .header_style{
            @include fj;
            line-height: 2rem;
            span:nth-of-type(1){
                @include sc(.7rem, #666);
            }
            .more_type{
                span:nth-of-type(1){
                    @include sc(.6rem, #aaa);
                    width: 10rem;
                    display: inline-block;
                    text-align: right;
                    vertical-align: middle;
                }
                svg{
                    @include wh(.5rem, .5rem);
                    fill: #ccc;
                }
            }
        }
        .hongbo{
            @include fj;
            border-top: 0.025rem solid #f5f5f5;
            span{
                @include sc(.6rem, #aaa);
                line-height: 2rem;
                svg{
                    @include wh(.5rem, .5rem);
                    vertical-align: middle;
                    fill: #ccc;
                }
            }
            span:nth-of-type(2){
                color: #aaa;
            }
        }
        .support_is_available{
            span{
                color: #666;
            }
        }
    }
    #amap-main{
      height: 19rem;
    }
    .food_list{
        background-color: #fff;
        flex:1;
        height: 19rem;
        header{
            padding: .7rem;
            border-bottom: 0.025rem solid #f5f5f5;
            text-align: center;
            img{
                @include wh(1.2rem, 1.2rem);
                vertical-align: middle;
            }
            span{
                @include sc(.6rem, #7a7a83);
            }
        }
        .food_list_ul{
            padding-top: .5rem;
        }
        .food_item_style{
            @include fj;
            line-height: 1.8rem;
            padding: 0 1.7rem;
            span,p{
                @include sc(.65rem, #666);
            }
            .food_name{
                width: 9rem;
            }
            .num_price{
                @include sc(.65rem, #666);
                flex: 1;
                @include fj;
                align-items: center;
                span:nth-of-type(1){
                    color: #f60;
                }
            }
        }
        .total_price{
            border-top: 0.025rem solid #f5f5f5;
        }
    }
    .confrim_order{
        display: flex;
        position: fixed;
        bottom: 0;
        width: 100%;
        height: 2.4rem;
        p{
            line-height: 2.4rem;
            @include sc(.65rem, #fff);
        }
        p:nth-of-type(1){
            background-color: #484f55;
            flex: 5;
            padding-left: .7rem;
        }
        p:nth-of-type(2){
            flex: 2;
            background-color: #1a99fd;
            text-align: center;
        }
    }
    .cover{
        position: fixed;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: rgba(0,0,0,.3);
        z-index: 203;
    }
    .choose_type_Container{
        min-height: 10rem;
        background-color: #fff;
        position: fixed;
        bottom: 0;
        width: 100%;
        z-index: 204;
        header{
            background-color: #fafafa;
            @include sc(.7rem, #333);
            text-align: center;
            line-height: 2rem;
        }
        ul{
            li{
                @include fj;
                padding: 0 .7rem;
                line-height: 2.5rem;
                align-items: center;
                span{
                    @include sc(.7rem, #ccc);
                }
                svg{
                    @include wh(.8rem, .8rem);
                    fill: #eee;
                }
            }
            .choose{
                span{
                    color: #333;
                }
                svg{
                    fill: #4cd964;
                }
            }
        }
    }
    .fade-enter-active, .fade-leave-active {
        transition: opacity .3s;
    }
    .fade-enter, .fade-leave-active {
        opacity: 0;
    }
    .slid_up-enter-active, .slid_up-leave-active {
        transition: all .3s;
    }
    .slid_up-enter, .slid_up-leave-active {
        transform: translate3d(0,10rem,0)
    }
    .router-slid-enter-active, .router-slid-leave-active {
        transition: all .4s;
    }
    .router-slid-enter, .router-slid-leave-active {
        transform: translate3d(2rem, 0, 0);
        opacity: 0;
    }
</style>
