<template>
    <header>
        <div class="container">
            <div class="header_body">
                <a class="logo" href="#"> <img src="../assets/icons8-logo.png" alt="logo"> </a>
                <div class="header_burger" :class="{active: isActive}" @click="toogleClass">
                    <span></span>
                </div>
                <nav class="header_menu" :class="{active: isActive}">
                    <ul class="header_list">
                        <li >
                            <router-link @click="isActive = false" class="header_item" to="/">Currency</router-link> 
                        </li>
                        <li >
                            <router-link @click="isActive = false" class="header_item" to="/about">Calculator</router-link>
                        </li>
                    </ul>
                </nav>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    data () {
        return {
            isActive: false,
        }
    },
    methods: {
        toogleClass () {
            if (this.isActive == false) {
                this.isActive = true
            } else {this.isActive = false}
        }
    }
}
</script>

<style lang="stylus" scoped>
    @media (max-width: 767px) 
        .header_list
            display: block
            width fit-content
            padding 0
        li
            margin-bottom  10px

        .header_burger
            display: block
            position: relative
            width: 30px
            height: 20px
            z-index: 3
        .header_burger span
            content ''
            background-color #fff
            position absolute
            width 100%
            height 2px
            top 9px
            left 0
            transition all 0.3s ease 0s
        .header_burger:before,
        .header_burger:after
            content ''
            background-color #fff
            position absolute
            width 100%
            height 2px
            left 0
            transition all 0.3s ease 0s
        .header_burger:before
            top 0
        .header_burger:after
            bottom 0

        .header_burger.active:before
            transform rotate(45deg)
            top 9px
        .header_burger.active:after
            transform rotate(-45deg)
            bottom 9px
        .header_burger.active span
            transform scale(0)

        .header_menu 
            position fixed
            top: -1000%
            left: 0
            width: 100%
            height: 100%
            background-color: #EEEEEE
            padding-top:  70px
            
        .header_menu.active
            top 0
            transition all 0.3s ease 0s 

    @media (min-width: 768px) 
        .header_burger
            display: none
        .header_list
            display: flex
            

    img
        height 50px

    header
        position fixed
        top 0
        left 0
        z-index 50
        width 100%
        
    header:before
        content ''
        position absolute
        top 0
        left 0
        width 100%
        height 100%
        z-index 2
        
        background #393E46

    .logo
        z-index 3

    .header_body
        position relative

        display flex
        justify-content space-between

        height 50px
        align-items center

    .header_list
        // display flex
        justify-content space-between
        position relative
        z-index 5
      
    .header_item
        margin-left 25px
        font-size 18px

    li
        list-style-type: none

</style>