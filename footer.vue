<template>
    <footer>
        <section class="footer_logo">
            <div>
                <a href="/">
                    <img alt="Property Logo" class="site_logo" src="//codecloud.cdn.speedyrails.net/sites/5afb34e36e6f646e4a5d0000/image/png/1521831709000/cambridgelogo@3x.png"/>   
                </a>
            </div>
            <div class="cambridge_logo">
                <a href="https://www.cambridge-centre.com/" target="_blank">
                    <img alt="Cambridge Shopping Centre Logo" src="//codecloud.cdn.speedyrails.net/sites/5afb34e36e6f646e4a5d0000/image/png/1522181927000/cambridgecentreoriginallogo.png">
                </a>
            </div>
            <div>
                <a href="https://www.morguard.com/news-knowledge/posts/cse2017-silverwin" target="_blank">
                    <img src="//codecloud.cdn.speedyrails.net/sites/5afb34e36e6f646e4a5d0000/image/png/1539965304000/logo.png" class="morguard_safety" alt="Safest Employees Logo">
                </a>
            </div>
            <div class="footer_management">
                <a href="http://www.morguard.com/" target="_blank">
                    <img class="management_logo" src="//codecloud.cdn.speedyrails.net/sites/5afb34e36e6f646e4a5d0000/image/png/1520542263000/morguard logo.png" alt="Morguard Logo"/>
                </a>
            </div>
        </section>
        <section class="footer_menu hidden_phone">
            <div class="main_container ">
                <ul class="footer_site_map hidden_phone">
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
    define(["Vue", "vuex", "moment", "moment-timezone", "vue-moment", "vue!search-component"], function (Vue, Vuex, moment, tz, VueMoment, SearchComponent) {
        return Vue.component("footer-component", {
            template: template, // the variable template will be injected,
            data: function data() {
                return {
                    suggestionAttribute: 'name',
                    search: '',    
                }
            },
            props:['social_media'],
            computed: {
                ...Vuex.mapGetters([
                    'property',
                    'processedStores'
                ]),
                copyright_year() {
                    return moment().year();
                }
            },
            methods: {
                onOptionSelect(option) {
                    console.log('Selected option:', option);
                    this.$nextTick(function() {
                        this.search = ""
                    });
                    this.$router.push("/stores/" + option.slug);
                }
            }
        });
    });
</script>