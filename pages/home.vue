<template>
	<div class="page">
    <Row v-show="directory" class="directory">
      <Icon type="ios-close-circle-outline" size="50" @click="closeDirectory"/>
      <Col
        class="directory-list"
        span="8"
        v-for="(item, index) in contentItemline"
        :key="index"
      >
        <div class="directory-item">
          <a :href="item.to">
            <div class="img">
              <img :src="item.img"/>
            </div>
            <div class="text">
              <h1>{{item.title}}</h1>
              <p>AUTOHOR: {{item.author}}</p>
            </div>
          </a>
        </div>
      </Col>
    </Row>

    <div class="left-box" v-show="!contentItem">
      <a href="#" class="logo"></a>
      <p>Warm little family</p>
      <h1>
        Suiyi Ｉ  Lᵒᵛᵉᵧₒᵤ
        <br/>
        Rourou <span>❥</span>
      </h1>
      <ul>
        <li><a v-bind:class="{active: selectedHone}" @click="onSelectedHone">HOME</a></li>
        <li><a v-bind:class="{active: selectedAbout}" @click="onSelectedAbout">ABOUT</a></li>
        <li><a v-bind:class="{active: selectedContact}" @click="onSelectedContact">CONTACT</a></li>
      </ul>
    </div>

    <div class="right-box">
      <div v-swiper:mySwiper="swiperOption">
        <div class="swiper-wrapper content">
          <div
            class="swiper-slide"
            v-for="(item, index) in contentItemline"
            :key="index"
          >
            
            <div v-bind:class="{active: contentItem}" class="content-item">
              <img :src="item.img" />
              <div class="item-text">
                <div class="line">
                  <div></div>
                  <p>
                    ROLE
                    <br/>
                    {{item.role}}
                  </p>
                  <p>
                    TIME
                    <br/>
                    {{item.time}}
                  </p>
                  <p>
                    AUTHOR
                    <br/>
                    {{item.author}}
                  </p>
                  <div></div>
                </div>
                <div class="title">
                  <h1>{{item.title}}</h1>
                  <Button @click="openWeb(item)" v-show="!contentItem" type="text" ghost>
                    {{item.button}}
                    <Icon type="ios-arrow-forward" size="25" />
                  </Button>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="on-switch" v-show="!contentItem">
          <div class="swiper-button-prev">
            <Icon type="ios-arrow-up" size="35" />
          </div>
          <Icon type="ios-apps-outline" size="35" @click="openDirectory" />
          <div class="swiper-button-next">
            <Icon type="ios-arrow-down" size="35" />
          </div>
        </div>
      </div>
    </div>
	</div>
</template>
	
<script>
export default {
  data () {
    return {
      directory: false,
      selectedHone: true,
      selectedAbout: false,
      selectedContact: false,

      contentItem: false,
      contentItemline: [
        {
          title: '111',
          img: 'https://img.zcool.cn/community/01293b5c6e22dfa801213f26c06f98.jpg@1280w_1l_0o_100sh.jpg',
          button: 'open case',
          role: 'animation',
          time: '2019',
          author: 'Rou rou',
          to: '/webSet/first'
        },
        {
          title: '222',
          to: '/webSet/ssss'
        },
        {
          title: '333',
          to: ''
        },
        {
          title: '444',
          to: ''
        },
        {
          title: '555',
          to: ''
        },
        {
          title: '666',
          to: ''
        },
        {
          title: '777',
          to: ''
        },
        {
          title: '888',
          to: ''
        }
      ],

      swiperOption: {
        direction: 'vertical',
        mousewheel: true,
        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev'
        }
      }
    }
  },
  methods: {
    onSelectedHone () {
      this.selectedHone = true
      this.selectedAbout = false
      this.selectedContact = false
    },
    onSelectedAbout () {
      this.selectedHone = false
      this.selectedAbout = true
      this.selectedContact = false
    },
    onSelectedContact () {
      this.selectedHone = false
      this.selectedAbout = false
      this.selectedContact = true
    },
    openWeb (item) {
      this.contentItem = true
      setTimeout(() => {
        if (item.title === '111') {
          this.$router.push({ path: item.to })
        } else {
          this.$router.push({ path: item.to })
        }
      }, 1000)
    },
    openDirectory () {
      this.directory = true
    },
    closeDirectory () {
      this.directory = false
    },
    handleScroll () {
      var scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop
      console.log(scrollTop)
    }
  },
  mounted () {
    window.addEventListener('scroll', this.handleScroll)
  }
}
</script>
<style lang="scss" scoped>
.page {
	&:after {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    width: 64.1145833333vw;
    padding-top: 40vw;
    background: #f0f0f0;
    transform: rotate(-31deg) translate3d(-3.5%, -63.6%, 0);
    z-index: -1;
	}
  .directory {
    color: #000;
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    z-index: 100;
    background-color: rgba(0, 0, 0, 0.616);
    padding: 75px 250px;
    i {
      position: fixed;
      top: 0;
      right: 0;
      margin: 30px;
    }
    .directory-list {
      text-align: -webkit-center;
      .directory-item {
        text-align: center;
        margin-bottom: 30px;
        position: relative;
        width: 350px;
        height: 250px;
        border: 8px solid #fff;
        overflow: hidden;
        a {
          width: 100%;
          &:hover {
            .img {
              transform: translateX(100%);
              transition: all 0.35s ease-in-out;
            }
            .text {
              transform: translateX(0);
              opacity: 1;
              transition: all 0.35s ease-in-out;
            }
          }
          .img {
            transform: translateX(0);
            transition: all 0.35s ease-in-out;
            width: 100%;
            height: 100%;
            img {
              height: 100%;
            }
          }
          .text {
            transform: translateX(-100%);
            background: #333333;
            opacity: 0;
            transition: all 0.35s ease-in-out;
            position: absolute;
            top: 0;
            bottom: 0;
            left: 0;
            right: 0;
            text-align: center;
            color: rgb(255, 255, 255);
            h1 {
              margin-top: 25px;
              padding: 5px;
              background-color: rgb(24, 24, 24);
            }
            p {
              padding: 8px;
              background-color: rgb(42, 42, 42);
            }
          }
        }
      }
    }
  }
	.left-box {
    position: fixed;
    left: 80px;
    top: 80px;
    z-index: 10;
    .logo {
      background-image: url('http://edwindejongh.co/portfolio2017/wp-content/themes/semplice-child/images/logo.png');
      display: inline-block;
	    background-size: cover;
	    width: 45px;
	    height: 60px;
    }
    p {
      margin-top: 60px;
      font-size: 18px;
      color: #183df2;
      font-weight: 999;
      margin-bottom: 20px;
    }
    h1 {
      color: #000;
      font-size: 50px;
      line-height: 55px;
      font-weight: 999;
      span {
        color: #f00;
      }
    }
    ul {
      margin-top: 300px;
      li {
        a {
          font-weight: 999;
					line-height: 35px;
          font-size: 16px;
          position: relative;
					color: #000000;
					&:hover {
						color: #183df2;
					}
      	}
      	.active {
          &:after {
            content: '';
            position: absolute;
            width: 100%;
            left: 0;
            top: 50%;
            background: #183df2;
            height: 4px;
            margin-top: -1px;
          }
        }
      }
    }
	}
  
  .right-box {
    top: 0;
    position: fixed;
    right: 0;
    left: 0;
    width: 100%;
    height: 100%;
    .swiper-container {
      width: 100%;
      height: 100%;
      .content {
        width: 100%;
        height: 100%;
        .content-item {
          box-shadow: 0 30px 60px rgba(0, 0, 0, 0.35);
          background-color: rgb(0, 187, 56);
          width: 73%;
          margin-left: 28%;
          height: 80%;
          margin-top: 5%;
          margin-bottom: 5%;
          transition: all .5s;
          position: relative;
          overflow: hidden;
          &:hover {
            img {
              transform: scale(1);
              transition: all 0.8s cubic-bezier(0.37, 0.045, 0.105, 0.8);
            }
          }
          img {
            position: absolute;
            transform: scale(1.2);
            z-index: 1;
            width: 100%;
            transition: all 0.8s cubic-bezier(0.37, 0.045, 0.105, 0.8);
          }
          .item-text {
            width: 100%;
            height: 100%;
            position: absolute;
            z-index: 100;
            color: rgb(255, 255, 255);
            display: flex;
            flex-direction: row;
            .line {
              position: absolute;
              top: 50px;
              left: 35px;
              div {
                margin-left: 10px;
                width: 1px;
                height: 240px;
                background-color: rgba(80, 80, 80, 0.65);
              }
              p {
                font-size: 15px;
                margin: 15px 0;
              }
            }
            .title {
              text-align: center;
              margin: 0 auto;
              h1 {
                font-size: 150px;
                margin-top: 250px;
              }
              button {
                font-size: 20px;
                border-radius: 100px;
                box-shadow: inset 0 0 0 2px #ffffff;
                color: #fff;
                transition: all 0.2s cubic-bezier(0.15, 0.005, 0.155, 1);
                overflow: hidden;
                padding: 10px 35px 15px;
                position: relative;
                &:after {
                  content: '';
                  position: absolute;
                  left: 0;
                  top: 0;
                  height: 100%;
                  width: 120%;
                  background: #ffffff;
                  transition: all 0.25s cubic-bezier(0.15, 0.005, 0.155, 1);
                  transform: skew(-10deg) translate3d(-120%, 0, 0);
                  z-index: -1;
                }
                &:hover {
                  color: #183df2;
                  &:after {
                    transform: skew(-10deg) translate3d(-10%, 0, 0);
                  }
                }
              }
            }
          }
        }
        .active {
          width: 90%;
          height: 790px;
          margin: 65px 5%;
        }
      }
      .on-switch {
        position: absolute;
        top: 50%;
        left: 27%;
        width: 35px;
        height: 150px;
        margin-top: -60px;
        z-index: 11;
        background-color: #fff;
        i {
          margin-top: 56px;
        }
        .swiper-button-prev {
          background-image: url('');
          left: 0;
          right: 0;
          position: absolute;
          top: 0;
          width: 35px;
          height: 50px;
          margin-top: 0;
          z-index: 15;
          cursor: pointer;
          i {
            margin: 0 auto;
          }
        }
        .swiper-button-next {
          background-image: url('');
          left: 0;
          right: 0;
          position: absolute;
          top: 100px;
          bottom: 0;
          width: 35px;
          height: 50px;
          margin-top: 0;
          z-index: 15;
          cursor: pointer;
          i {
            margin: 16px auto 0;
          }
        }
      }
    }
  }
}
</style>