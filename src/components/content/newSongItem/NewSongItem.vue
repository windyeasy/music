<template>
    <!-- 最新item组件 -->
  <div class="newSong-item">
    <div class="item-left">
        <img :src="songItem.picUrl" alt="">
        <i class="iconfont icon-bofang"></i>
    </div>
    <div class="item-right">
        <div class="song-title">{{songItem.name}}</div>
        <div class="singer">{{songItem.song.artists | singer}}</div>
    </div>
  </div>
</template>

<script>
export default {
    props: {
        songItem: {
            type: Object,
            default() {
                return {}
            }
        }
    },
    name: 'NewSongItem',
    filters: {
        singer(value){
            const strArr = value.reduce((oldValue, newValue) => {
                return oldValue + newValue.name + ' '
            }, '').split(' ')
            let str = strArr.splice(0, strArr.length - 1).join('/')
            return str
        }
    }
}
</script>

<style lang="less" scoped>
 .newSong-item {
    width: 32%;
    height: 65px;
    flex-shrink: 0;
    margin-right: 15px;
}
 .newSong-item:hover {
    background-color: #eee;
 }
.item-left, .item-right {
    margin-top: 10px;
    float: left;
    height: 45px;

}
.item-left {
    
    margin-right: 8px;
    position: relative;
    .iconfont {
        font-size: 20px;
        position: absolute;
        width: 20px;
        height: 20px;
        left: 0;
        right: 0;
        bottom: 0;
        top: 0;
        margin: auto;
        background-color: red;
        color: #fff;
        border-radius: 50%;
        box-sizing: border-box;
    }
}
.item-left img {
    width: 45px;
    height: 45px;
    border-radius: 5px;
}
.item-right {
    width: 80%;
    font-size: 14px;
    .song-title {
        margin-bottom: 5px;
    }
    .singer {
        color: #5f5f5f;
        font-size: 13px;
    }
    .song-title, .singer {
        width: 100%;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
    }
}
</style>