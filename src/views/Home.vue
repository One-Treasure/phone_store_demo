<template>
  <div class="home">
    <van-row>
      <van-col span="24">
        <van-tabs @click="onClick">
          <van-tab v-for="index in categories.length" :title="categories[index-1].name" class="tab"></van-tab>
          <van-card v-for="(item,index) in phones"
                    :price="item.price"
                    :desc="item.desc"
                    :title="item.title"
                    :thumb="item.thumb"
          >
            <template #tags>
              <van-tag color="#f2826a" style="margin-left: 5px;">720P珍珠屏</van-tag>
              <van-tag color="#f2826a" style="margin-left: 5px;">Micro USB接口</van-tag>
            </template>
            <template #footer>
              <van-button round type="info" size="mini" @click="buy(index)">购买</van-button>
            </template>
          </van-card>
        </van-tabs>
      </van-col>
    </van-row>

    <van-sku
      v-model="show"
      :sku="sku"
      :goods="goods"
      :hide-stock="sku.hide_stock"
      @buy-clicked="onBuyClicked"
    >
      <template #sku-actions="props">
        <div class="van-sku-actions">

          <!--直接出发sku内部时间，通过内部事件执行onBuyClicked回调-->
          <van-button
            square
            size="large"
            type="danger"
            @click="props.skuEventBus.$emit('sku:buy')"
          >
            买买买
          </van-button>
        </div>
      </template>
    </van-sku>

  </div>
</template>

<script>
  export default {
    data() {
      return {
        categories: [
          {
            name: "魅焰红",
            type: 1
          },
          {
            name: "极光蓝",
            type: 2
          },
          {
            name: "铂光金",
            type: 3
          },
          {
            name: "幻夜黑",
            type: 4
          }
        ],
        phones:[
          {
            id: 1,
            price: "2800.00",
            desc: "魅焰红",
            title: "Honor 8A",
            thumb: "../static/e84a2e03-7f19-41d2-98a5-a5c16b7e252d.jpg",
            tag: [
              {
                name: "720P珍珠屏",
              },
              {
                name: "Micro USB接口",
              }
            ]
          },
          {
            id: 2,
            price: "2800.00",
            desc: "极光蓝",
            title: "Honor 10 青春版",
            thumb: "../static/8f0bd0d0-a11e-4185-927e-04b54ff4a1bd.jpg",
            tag: [
              {
                name: "720P珍珠屏",
              },
              {
                name: "EMUI9 Lite",
              }
            ]
          },
          {
            id: 3,
            price: "3450.00",
            desc: "铂光金",
            title: "Honor V20",
            thumb: "../static/fd7fee3c-a35c-477b-b007-9fda6e9c589a.jpg",
            tag: [
              {
                name: "720P珍珠屏",
              },
              {
                name: "Micro USB接口",
              }
            ]
          },
          {
            id: 4,
            price: "4550.00",
            desc: "幻夜黑",
            title: "HUAWEI Mate 20 Pro",
            thumb: "../static/cb819ad9-ec6f-4123-a4e9-aa629e2f8224.jpg",
            tag: [
              {
                name: "720P珍珠屏",
              },
              {
                name: "Micro USB接口",
              }
            ]
          },
          {
            id: 5,
            price: "5450.00",
            desc: "魅焰红",
            title: "HUAWEI nova 5 Pro",
            thumb: "../static/8a0f5be0-3c78-4f23-b58b-dc2a92f1f95a.jpg",
            tag: [
              {
                name: "720P珍珠屏",
              },
              {
                name: "Micro USB接口",
              }
            ]
          },
          {
            id: 6,
            price: "8700.00",
            desc: "极光蓝",
            title: "HUAWEI P30",
            thumb: "../static/6dcad185-315f-40f0-87f2-52910f49c8b7.jpg",
            tag: [
              {
                name: "720P珍珠屏",
              },
              {
                name: "Micro USB接口",
              }
            ]
          },
          {
            id: 7,
            price: "8988.00",
            desc: "铂光金",
            title: "HUAWEI P30 Pro",
            thumb: "../static/b12a46a9-3738-49ab-ab3a-6878539bd76b.jpg",
            tag: [
              {
                name: "720P珍珠屏",
              },
              {
                name: "Micro USB接口",
              }
            ]
          },
          {
            id: 8,
            price: "2760.00",
            desc: "幻夜黑",
            title: "HUAWEI 畅想9 Plus",
            thumb: "../static/15a5dcf2-4b50-41a0-93e8-08df97c21341.jpg",
            tag: [
              {
                name: "720P珍珠屏",
              },
              {
                name: "Micro USB接口",
              }
            ]
          },
          {
            id: 9,
            price: "7254.00",
            desc: "魅焰红",
            title: "SAMSUNG G S10",
            thumb: "../static/a4f0cef8-59da-4f7c-abfa-d373f6648035.jpg",
            tag: [
              {
                name: "720P珍珠屏",
              },
              {
                name: "Micro USB接口",
              }
            ]
          },
          {
            id: 10,
            price: "2889.00",
            desc: "极光蓝",
            title: "OPPO K3",
            thumb: "../static/efc31538-a1f0-4dba-a673-4369f17e5708.jpg",
            tag: [
              {
                name: "720P珍珠屏",
              },
              {
                name: "Micro USB接口",
              }
            ]
          }
        ],
        show: false,
        sku: '',
        goods: ''
      }
    },
    methods: {
      onClick(index) {
        switch(index) {
          case 0:
            this.phones = [
                {
                id: 1,
                price: "2800.00",
                desc: "魅焰红",
                title: "Honor 8A",
                thumb: "../static/e84a2e03-7f19-41d2-98a5-a5c16b7e252d.jpg",
                tag: [
                  {
                    name: "720P珍珠屏",
                  },
                  {
                    name: "Micro USB接口",
                  }
                ]
              },
              {
                id: 5,
                price: "5450.00",
                desc: "魅焰红",
                title: "HUAWEI nova 5 Pro",
                thumb: "../static/8a0f5be0-3c78-4f23-b58b-dc2a92f1f95a.jpg",
                tag: [
                  {
                    name: "720P珍珠屏",
                  },
                  {
                    name: "Micro USB接口",
                  }
                ]
              },
              {
                id: 9,
                price: "7254.00",
                desc: "魅焰红",
                title: "SAMSUNG G S10",
                thumb: "../static/a4f0cef8-59da-4f7c-abfa-d373f6648035.jpg",
                tag: [
                  {
                    name: "720P珍珠屏",
                  },
                  {
                    name: "Micro USB接口",
                  }
                ]
              }
            ]
            break;
          case 1:
            this.phones = [
              {
                id: 2,
                price: "2800.00",
                desc: "极光蓝",
                title: "Honor 10 青春版",
                thumb: "../static/8f0bd0d0-a11e-4185-927e-04b54ff4a1bd.jpg",
                tag: [
                  {
                    name: "720P珍珠屏",
                  },
                  {
                    name: "EMUI9 Lite",
                  }
                ]
              },
              {
                id: 6,
                price: "8700.00",
                desc: "极光蓝",
                title: "HUAWEI P30",
                thumb: "../static/6dcad185-315f-40f0-87f2-52910f49c8b7.jpg",
                tag: [
                  {
                    name: "720P珍珠屏",
                  },
                  {
                    name: "Micro USB接口",
                  }
                ]
              },
              {
                id: 10,
                price: "2889.00",
                desc: "极光蓝",
                title: "OPPO K3",
                thumb: "../static/efc31538-a1f0-4dba-a673-4369f17e5708.jpg",
                tag: [
                  {
                    name: "720P珍珠屏",
                  },
                  {
                    name: "Micro USB接口",
                  }
                ]
              }
            ]
            break;
          case 2:
            this.phones = [
              {
                id: 3,
                price: "3450.00",
                desc: "铂光金",
                title: "Honor V20",
                thumb: "../static/fd7fee3c-a35c-477b-b007-9fda6e9c589a.jpg",
                tag: [
                  {
                    name: "720P珍珠屏",
                  },
                  {
                    name: "Micro USB接口",
                  }
                ]
              },
              {
                id: 7,
                price: "8988.00",
                desc: "铂光金",
                title: "HUAWEI P30 Pro",
                thumb: "../static/b12a46a9-3738-49ab-ab3a-6878539bd76b.jpg",
                tag: [
                  {
                    name: "720P珍珠屏",
                  },
                  {
                    name: "Micro USB接口",
                  }
                ]
              }
            ]
            break;
          case 3:
            this.phones = [
              {
                id: 4,
                price: "4550.00",
                desc: "幻夜黑",
                title: "HUAWEI Mate 20 Pro",
                thumb: "../static/cb819ad9-ec6f-4123-a4e9-aa629e2f8224.jpg",
                tag: [
                  {
                    name: "720P珍珠屏",
                  },
                  {
                    name: "Micro USB接口",
                  }
                ]
              },
              {
                id: 8,
                price: "2760.00",
                desc: "幻夜黑",
                title: "HUAWEI 畅想9 Plus",
                thumb: "../static/15a5dcf2-4b50-41a0-93e8-08df97c21341.jpg",
                tag: [
                  {
                    name: "720P珍珠屏",
                  },
                  {
                    name: "Micro USB接口",
                  }
                ]
              }
            ]
            break;
        }
      },
      buy(index) {
        this.show = true
        this.goods = {
          picture: "../static/e84a2e03-7f19-41d2-98a5-a5c16b7e252d.jpg"
        }
        this.sku = {
          tree: [
            {
              k: "规格",
              v: [
                {
                  id: 1,
                  name: "32G",
                  imgUrl: "../static/e84a2e03-7f19-41d2-98a5-a5c16b7e252d.jpg",
                  previewImgUrl: "../static/e84a2e03-7f19-41d2-98a5-a5c16b7e252d.jpg"
                },
                {
                  id: 2,
                  name: "64G",
                  imgUrl: "../static/e84a2e03-7f19-41d2-98a5-a5c16b7e252d.jpg",
                  previewImgUrl: "../static/e84a2e03-7f19-41d2-98a5-a5c16b7e252d.jpg"
                }
              ],
              k_s: "s1"
            }
          ],
          list: [
            {
              s1: 1,
              price: 280000,
              stock_num: 5
            },
            {
              s1: 2,
              price: 320000,
              stock_num: 5
            }
          ],
          price: "2800.00",
          stock_num: 10,
          none_sku: false,//是否隐藏规格
          hide_stock: false//是否隐藏库存
        }
      },
      onBuyClicked(item) {
        console.log(item)
        this.$store.state.specsId = item.selectedSkuComb.s1
        this.$store.state.quantity = item.selectedNum
        this.$router.push('/addressList')
      }
    }
  };

</script>
