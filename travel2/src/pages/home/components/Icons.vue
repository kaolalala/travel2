<template>
    <div class="icons">
        <swiper :options="swiperOption">
            <swiper-slide v-for="(page, index) of pages" :key="index">
                <div class="icon" v-for="item of page" :key="item.id">
                    <div class="icon-img">
                        <img class="icon-img-content" :src="item.imgUrl">
                    </div>
                    <p class="icon-desc">{{item.desc}}</p>
                </div>
            </swiper-slide>
        </swiper>
    </div>
</template>

<script>
export default {
    name: 'HomeIcons',
    props: {
        list: Array
    },
    data () {
        return {
            swiperOption: {
                autoplay: false
            }
        }
    },
    // data () {
    //     return {
    //         iconList: [{
    //             id: '0001',
    //             imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
    //             desc: '景点门票'
    //         }, {
    //             id: '0002',
    //             imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png',
    //             desc: '广州必游'
    //         }, {
    //             id: '0003',
    //             imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png',
    //             desc: '动植物园'
    //         }, {
    //             id: '0004',
    //             imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20193/a40ee278d67000f2a29d2e20f6a029b3.png',
    //             desc: '自然风光'
    //         }, {
    //             id: '0005',
    //             imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png',
    //             desc: '一日游'
    //         }, {
    //             id: '0006',
    //             imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/3e/86314b2af03b7502.png',
    //             desc: '水上乐园'
    //         }, {
    //             id: '0007',
    //             imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/3e/86314b2af03b7502.png',
    //             desc: '亲子游'
    //         }, {
    //             id: '0008',
    //             imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20193/184e261814a5d07a5d3d08cd29cf590d.png',
    //             desc: '长隆度假区'
    //         }, {
    //             id: '0009',
    //             imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20193/c032ae43b15a3dac34b5e07bb0e46850.png',
    //             desc: '广州塔'
    //         }]
    //     }
    // },
    computed: {
        pages () {
            const pages = [];
            this.list.forEach((item, index) => {
                const page = Math.floor(index / 8);
                if(!pages[page]) {
                    pages[page] = [];
                }
                pages[page].push(item);
            })
            return pages;
        }
    }
}
</script>

<style lang="stylus" scoped>
    @import '~styles/varibles.styl'
    @import '~styles/mixins.styl'
    .icons >>> .swiper-container
        width: 100%
        height: 0
        padding-bottom: 50%
    .icons
        margin-top: .1rem;
        .icon
            position: relative
            width: 25%
            height: 0
            padding-bottom: 25%
            float: left
            overflow: hidden
            .icon-img
                position: absolute
                top: 0
                left: 0
                right: 0
                box-sizing: border-box
                padding: .05rem
                bottom: .44rem
                .icon-img-content
                    display: block
                    margin: 0 auto
                    height: 100%
            .icon-desc
                position: absolute
                left: 0
                right: 0
                bottom: 0
                line-height: .44rem
                height: .44rem
                text-align: center
                color: $darkTextColor
                ellipsis()
</style>