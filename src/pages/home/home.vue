<style lang="less" scoped>
.home{

}
.item{
  background: #fff;
  margin-top:20px;
  padding: 20px 30px;
  padding-top: 0;
  .item-title{
    line-height: 50px;
  }
  .item-content{
    .item-left{
      float: left;
      width: 35%;
      img{
        width:100%;
        cursor: pointer;
      }
    }
    .item-right{
      float: right;
      width: 62%;
    }
  }
}
.row{
  margin-top:10px;
  width: 100%;
  .row-left{
    float: left;
    width: 15%;
    text-align: right;
    color: #555;
  }
  .row-right{
    float: right;
    width: 82%;
  }
}
.text{
  .time{
    color: #555;
    font-size: 14px;
    margin-left: 10px;
  }
}

a{
  text-decoration: none;
  color: #555;
  cursor: pointer;
  &:hover{
    color: #1D8CE0;
  }
}
.video-img img{width:100%;padding: 5px;}
</style>
<template>
<div class="home">
  <div class="item">
    <div class="item-title"><router-link to="/trailer">最新预告</router-link></div>
    <div class="item-content clearfix">
      <div class="item-left"><img src="src/assets/images/home-p1.webp" alt="" @click="showVideo(trailerData.url)"/></div>
      <div class="item-right">
        <div class="row clearfix">
          <div class="row-left">电影名称:</div>
          <div class="row-right"><router-link :to="{path:'/detail',query:Object.assign({last:'',lastName:''},trailerData)}">{{trailerData.name}}</router-link></div>
        </div>
        <div class="row clearfix">
          <div class="row-left">上映日期:</div>
          <div class="row-right">{{trailerData.time}}</div>
        </div>
        <div class="row clearfix">
          <div class="row-left">电影简介:</div>
          <div class="row-right" v-html="trailerData.intro"></div>
        </div>
      </div>
    </div>
  </div>
  <div class="item">
    <div class="item-title"><router-link to="/article">精彩影评</router-link></div>
    <div class="item-content">
      <div class="text"><span class="name"><router-link :to="{path:'/detail',query:Object.assign({last:'',lastName:''},articleData)}">{{articleData.name}}</router-link></span> <span class="time">{{articleData.time}}</span></div>
      <div class="article" v-html="articleData.content" >

      </div>
    </div>
  </div>
  <div class="item">
    <div class="item-title"><router-link to="/video">影评视频</router-link></div>
    <div class="item-content clearfix">
      <div class="video-img"><img src="src/assets/images/luogen.webp" alt="" @click="showVideo(videoData.url)"/></div>
      <div class="text"><span class="name"><router-link :to="{path:'/detail',query:Object.assign({last:'',lastName:''},videoData)}">{{videoData.name}}</router-link></span> <span class="time">{{videoData.time}}</span></div>
    </div>
  </div>
  <div class="item">
    <div class="item-title"><router-link to="/comment">评论专区</router-link></div>
    <ul class="item-content">
      <li v-for="item in commentData">
        <span>[{{item.type}}]</span>
        <span>{{item.time}}</span>
        <span><router-link to="/comment-detail">{{item.content}}</router-link></span>
      </li>
    </ul>
  </div>
<!-- video dialog -->
  <el-dialog title="视频播放" v-model="dialogVisible" size="">
    <div v-html="url"></div>
  </el-dialog>
</div>
</template>
<script>
export default {
  name: 'home',
  data () {
    return {
      trailerData:{
        name:"美女与野兽",
        time:"2017-03-17(中国大陆/美国)",
        url:'<embed height="415" width="544" quality="high" allowfullscreen="true" type="application/x-shockwave-flash" src="//static.hdslb.com/miniloader.swf" flashvars="aid=8382491&page=1" pluginspage="//www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash"></embed>',
        intro:"<p>贝儿（艾玛·沃森 Emma Watson 饰）和小镇上的其他女孩不同，是一个热爱阅读和幻想的姑娘，孔武有力英俊强壮的加斯顿（卢克·伊万斯 Luke Evans 饰）发誓要娶贝儿为妻，但贝儿却一眼看穿了他的自私和虚伪，拒不从命。某日，贝儿的父亲莫里斯（凯文·克莱恩 Kevin Kline 饰）迷路误打误撞之下来到了一座荒凉破败的城堡中，那里居住着样貌可怖半人半兽的野兽（丹·史蒂文斯 Dan Stevens 饰）。</p><p>因为偷摘了城堡里种植的玫瑰，莫里斯被野兽囚禁了起来，得知此消息的贝儿赶到城堡，要求和父亲作交换。就这样，贝儿开始了和野兽的同居生活。在会说话的茶壶太太（艾玛·汤普森 Emma Thompson 饰）、烛台卢米亚（伊万·麦克格雷格 Ewan McGregor 饰）和时钟葛士华（伊恩·麦克莱恩 Ian McKellen 饰）的照顾和帮助下，贝儿渐渐发现，野兽在丑陋的外表下，隐藏了一颗善良温柔的心。实际上，野兽的真实身份是一位王子，因受到了女巫的诅咒而沦落至此，而贝儿，是解除诅咒最后的，也是唯一的希望。</p>"
      },
      articleData:{
        name:"带着杀戮活下去很难",
        time:"2017-03-20",
        content:'<p>《金刚狼3》中，金刚狼罗根死了。他的死，印证了影片中一句话：带着杀戮活下去很难。</p><p>我看《金刚狼3》，感觉编导很鬼，让这最关键一句话隐身电视中。当时在一旅馆，罗根忙什么去了，留下X教授和劳拉在房间看电视，播放的电影里，剧中人说了一句话：带着杀戮活下去很难，这条路没有退路。如非特别敏感，谁会注意这“剧中剧”里的对白呢？当罗根死去，劳拉在其墓前重复这话时，我知道了，《金刚狼3》的主题在这。</p><p>影片的三个主要人物，就是上面提到的罗根、X教授和劳拉，类似祖孙三代那种。事实上，三人被邀留宿黑人家时，就是以祖父、父亲和女儿相称的。这种组合，让我想起《红灯记》里李奶奶对李铁梅说：你姓陈，我姓李，你爹他姓张！虽无血缘关系，却又视同祖孙：罗根小时候，被X教授的特殊学校收留，两人情同父子；劳拉是制作的出来，用的正是罗根的基因，等于是他女儿。</p><p>这是一部关于杀戮的影片，从头到尾都在追杀，被追杀者就是劳拉。为什么要杀她？这就要说到莱斯博士。此人领导一个团队，专门制作如罗根一般的变种人，目的是，利用其超强能力进行杀戮。所以影片中说，劳拉等不是人，而是产品；他们没有姓名，只有编号，例如劳拉，其编号是X23。但产品出了问题：他们不想战斗。不想战斗的士兵是无用的士兵，莱斯便要毁掉这批产品，对那些孩子实施安乐死。一护士想挽救他们，带着劳拉来找罗根。她认为，唯罗根有这能力，希望他带劳拉去“伊甸园”。莱斯团队岂能放过？于是就有了一路的追杀。</p><p>杀戮首先发生在汽车旅馆，莱斯团队杀了护士。再次发生在罗根等三人留宿的黑人家，该团队杀了X教授；曾照顾X教授的变种人，也被逼与敌同归于尽。最后发生在“伊甸园”，团队杀了罗根。被杀戮者中，除护士而外，其他三人都曾参与杀戮。之所以被杀戮，是因为曾经杀戮；一旦染指杀戮，便在劫难逃，这就回归影片的主题：带着杀戮活下去很难。</p><p>既如此，为什么还要杀戮？这是个很难讲清楚的问题。我想，是相信自己永远强大、能永远立于不败之地、永远不被杀戮吧？比如说，相信一种超强能力，如罗根一般变种人，或劳拉一般仿制变种人，他们都有超强的战斗力和自我愈合能力，在注入艾德曼合金后，以钢爪取代之前的骨爪，真正成为金刚狼。如果说，这就是原因，仿制变种人的莱斯及其团队，也当作如是观。</p><p>但既是一种能力就一定有衰减时。当你老了，头发白了，无论是罗根，还是X教授，还会跟年轻、盛年时一样吗？看到瘸腿、总是大口喘气、身上伤痕累累的罗根，看到患老年痴呆、呆坐轮椅上、连上厕所都要服侍的X教授，人们就知道，衰减一定会来临；一旦能力衰减，就会面临被杀戮。原来是：我为刀俎人为鱼肉，现在变成：人为刀俎我为鱼肉。影片中，罗根、X教授所面临的，不就是这样一种局面吗？</p><p>当然，还可注射“兴奋剂”来保持战斗力，就像罗根所做的那样。但你在强化自己时，敌人也没闲着。莱斯团队不但已使用变种人“机械手”，干脆还克隆一个金刚狼来对付罗根，两个金刚狼大战，令我想起《西游记》中的真假孙悟空。总之，你使出一招，他必还一招，就这么永远较量下去？——我怎么感觉，我在说当今世界的军备、或核武器竞赛？</p><p>所以，以杀戮还杀戮，以鲜血还鲜血，冤冤相报，不会有了时的。无论是罗根，还是X教授，都悟出这一点。如非意外卷入劳拉一事，开着网约车的罗根，原是打算赚够钱，买一艘“逐日号”，带着X教授远走他乡的。影片最温馨一段，是三人被邀留宿黑人家时，在那里，他们假扮祖孙三代，其乐融融。X教授对罗根说：生活就该这样，像一家人一样生活；你还有时间。意思是，让罗根“金盘洗手”。</p><p>但杀戮场，也是一个江湖啊。因自身的超强能力，还因过去的杀戮，让他们深感退出之难。X教授已在忏悔：这是我最美好的晚上，我不配拥有它。因为我做了一些事，不能说的。影片中隐约透露，X教授曾因故杀死他的学生。罗根何尝不如此？他身藏一颗艾德曼合金子弹，准备随时结束自己生命。在“伊甸园”时，罗根举着子弹对劳拉说，正是这个要我的命。杀戮太重，即便放下屠刀，也难做一介凡人的。</p><p>可以说，自有人类以来，杀戮从未停止过。发动杀戮的原因很多：生存、财产、权力、宗教……同时，人们为杀戮找了很多借口，比如说，杀坏人。在“伊甸园”，有一段对话很值得玩味。当时，罗根在睡梦中惊醒。劳拉问，是不是做噩梦？罗根答，是。劳拉说，我也做噩梦，我是被人伤害。罗根说，我是伤害别人。劳拉说，我也伤害过别人，但他们都是坏人。罗根说，其实都一样。这段对话表明：杀戮就是杀戮，杀好人是，杀坏人同样是——别说杀坏人不是杀戮！</p><p>罗根临死时，对着获救的劳拉等说，你们不要再战斗了。他说的其实是，你们不要再杀戮了。这是罗根的遗愿，一个曾经战无不胜、也杀人无数的金刚狼的遗愿。</p><p>影片的后段，杀戮者最终也被杀戮，包括莱斯，莱斯的重要帮手“机械手”，莱斯的最新产品、模仿罗根而制作的X24。这对所有杀戮者，都是一个警示——</p><p>带着杀戮活下去很难。</p><p>别再杀戮！</p>'
      },
      videoData:{
        name:"【金刚狼3】木鱼三分钟影评——一个十七年传奇的终结",
        time:"2017-03-14",
        url:'<embed height="415" width="544" quality="high" allowfullscreen="true" type="application/x-shockwave-flash" src="//static.hdslb.com/miniloader.swf" flashvars="aid=9153305&page=1" pluginspage="//www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash"></embed>',
      },
      commentData:[
        {
          type:"系统创建",
          content:"《金刚狼》讨论区",
          time:"2017-04-01"
        },
        {
          type:"系统创建",
          content:"《分裂》讨论区",
          time:"2017-04-01"
        }
      ],
      url:"test",
      dialogVisible: false
    }
  },
  methods:{
    showVideo(url){
      this.url=url;
      this.dialogVisible = true
    }
  }
}
</script>
