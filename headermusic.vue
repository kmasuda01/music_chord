<template>
    <div class="body">
        <div class="container">
            <div class="header">
                <div class="header_inner">
                    <p>My MUSIC CHORD</p>
                </div>
            </div>
            <nav class="nav">
                <div class="nav_inner">
                    <ul class="nav_list">
                        <li class="nav_item">
                            <a class="nav_char" href="#search">コード検索</a>
                        </li>
                        <li class="nav_item">
                            <a class="nav_char" href="#create">コード作成</a>
                        </li>
                        <li class="nav_item">
                            <a class="nav_char" href="#showmy">コード表示</a>
                        </li>
                    </ul>
                </div>
            </nav>
        <Body></Body>
        </div>
        <Footer></Footer>
    </div>
</template>

<script>
import Body from '@/components/bodymusic.vue'
import Footer from './footer.vue'
export default {
    components: {
    Body,
    Footer
  }
    // data(){
    //     return {
    //         title: "PortForio"
    //     }
    // }
}
</script>

<style scoped>
    .container{
    position: sticky;
}
.header{
    display: flex;
    align-items: center;
    justify-content: center;
    height: 11em;
    text-align: center;
}
.header_inner{
    padding: 40px;
    font-family: 'Amatic SC', cursive;
    font-size: 40px;
}
.nav{
    position: sticky;
    top: 0;
    z-index: 100;
    width: 100%;
    background-color: #fff;
}
.nav_list{
    padding:0;
    display: flex;
    justify-content: center;
    list-style: none;
}
.nav_item{
    margin: 0 40px;
}
.nav_char{
    text-decoration:none; 
    color: #BEBEBE;
}
a:hover{
    /* aタグのhoverクラスカーソル合わせると色変わる */
    color:black;
}
</style>