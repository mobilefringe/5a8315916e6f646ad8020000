<template>
    <footer>
        <section class="footer_logo">
            <div>
                <img alt="Property Logo" class="site_logo" src="//codecloud.cdn.speedyrails.net/sites/5a8315916e6f646ad8020000/image/png/1519944340000/logo-01.png"/>    
            </div>
            <div class="footer_social">
                <div class="social_icons">
                    <span v-for="item in social_media">
                        <a :href="item.url" target="_blank">
                            <i :class="item.iconClass" aria-hidden="true"></i>
                        </a>
                    </span>
                </div>    
            </div>
            <!--<div class="footer_search hidden_phone">-->
            <!--    <search-component v-model="search" :list="processedStores" :suggestion-attribute="suggestionAttribute" @select="onOptionSelect">-->
            <!--        <template slot="item" scope="option">-->
            <!--            <article class="media">-->
            <!--                <p>{{ option.data.name }}</p>-->
            <!--            </article>-->
            <!--        </template>-->
            <!--    </search-component>-->
            <!--</div>-->
        </section>
        <section class="footer_menu hidden_phone">
            <div class="main_container ">
                <ul class="footer_site_map hidden_phone">
                    <!--<router-link tag="li" to="/pages/cambridge-privacy-policy" exact>-->
                    <!--    <a>Privacy Policy</a>-->
                    <!--</router-link>-->
                    <li>
                        <a href="https://www.morguard.com/privacy/" target="_blank">Privacy Policy</a>
                    </li>
                    <router-link tag="li" to="/pages/cambridge-terms-conditions" exact>
                        <a>Terms & Conditions</a>
                    </router-link>  
                    <router-link tag="li" to="/jobs" exact>
                        <a>Jobs</a>
                    </router-link>
                </ul>
            </div>
        </section>
        <section class="footer_privacy">
            <div class="main_container">
                <p class="footer_desc">&#169; {{copyright_year}} {{property.name}} | Powered By <a href="//mallmaverick.com" target="_blank">Mall Maverick</a></p>
            </div>
        </section>
    </footer>
</template>

<script>
var _extends=Object.assign||function(e){for(var t=1;t<arguments.length;t++){var n=arguments[t];for(var o in n)Object.prototype.hasOwnProperty.call(n,o)&&(e[o]=n[o])}return e};define(["Vue","vuex","moment","moment-timezone","vue-moment","vue!search-component"],function(e,t,n){return e.component("footer-component",{template:template,data:function(){return{suggestionAttribute:"name",search:""}},props:["social_media"],computed:_extends({},t.mapGetters(["property","processedStores"]),{copyright_year:function(){return n().year()}}),methods:{onOptionSelect:function(e){console.log("Selected option:",e),this.$nextTick(function(){this.search=""}),this.$router.push("/stores/"+e.slug)}}})});
</script>