<template>
    <div class="postlist">
        <div class="posts">
            <ul>
                <li>
                    <div class="toobar">
                        <span>全部</span>
                        <span>精华</span>
                        <span>分享</span>
                        <span>问答</span>
                        <span>招聘</span>
                    </div>
                </li>
                <li v-for="post in posts">
                    <img :src='post.author.avatar_url' alt="">
                    <span class="allcount">
                        <span class="reply_count">{{ post.reply_count }}</span>/{{ post.visit_count }}
                    </span>
                    <span :class="[{
                        put_good: (post.good == true), put_top: (post.top == true),
                        'topiclist-tab': (post.good != true && post.top != true), }]">
<span>{{ post | tabFormatter }}</span>
                    </span>
                    <span>{{ post.title }}</span>
                    <span class="replytime">{{ post.last_reply_at | formatDate }}</span>
                </li>
            </ul>
        </div>
    </div>
</template>
<style scoped>
ul,
li {
    list-style: none;
    padding: 0;
    margin: 0;
}

img {
    height: 30px;
    vertical-align: middle;
    /*垂直对齐*/
}

.postlist {
    max-width: 90%;
    background-color: #fff;
    margin: 0 auto;
}

.toobar {
    background-color: #f6f6f6;
  
}
.toobar span {
    font-size: 14px;
    color: #80bd01;
    line-height: 40px;
    margin: 0 10px;
    cursor: pointer;
  }

  .toobar span:hover {
    color: #9e78c0;
  }
.posts {
    margin: 10px 0;

}

.allcount {
    color: #b4b4b4;
    font-size: 10px;
    width: 70px;
    display: inline-block;
    text-align: center;
}
ul li:not(:first-child) {
    padding: 9px;
    font-size: 15px;
    background-color: white;
    color: #333;
    border-top: 1px solid #f0f0f0;
  }
  li:not(:first-child):hover {
    background: #f5f5f5;;
  }
.reply_count {
    color: #9e78c0;
    font-size: 10px;
}

.replytime {
    float: right;
    color: #778087;
    font-size: 10px;
    padding-right: 10px;
}

.put_good,
.put_top {
    background: #80bd01;
    padding: 2px 4px;
    border-radius: 3px;
    color: #fff;
    font-size: 12px;
    margin-right: 10px;
}

.topiclist-tab {
    background-color: #e5e5e5;
    color: #999;
    padding: 2px 4px;
    border-radius: 3px;
    font-size: 12px;
    margin-right: 10px;
}
</style>

<script>
export default {
    data() {
        return {
            posts: [],
        }
    },
    methods: {
        getData() {
            this.$http.get('https://cnodejs.org/api/v1/topics')
                .then(res => {
                   
                    this.posts = res.data.data;
                })
                .catch(err => {
                    console.log(err);
                })
        }
    },

    beforeMount() {
      
            this.getData();/*在页面加载前获取数据*/
    }
}
</script>