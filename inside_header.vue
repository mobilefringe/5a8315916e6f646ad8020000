<template>
    <div class="inside_header_background">
        <div class="main_container">
            <div class="hours_container">
                <p class="hours_title">{{ $t("hours.hours-title") }}</p>
                <div>
                    <p>
                        {{ $t("hours.hours-mon") }}:<br/>
                        <span v-for="hour in weekdayHours">
                            {{hour.open_time | moment("h:mm a", timezone)}} - {{hour.close_time | moment("h:mm a", timezone)}}    
                        </span>
                    </p>
                </div>
                <div>
                    <p>
                        {{ $t("hours.hours-sat") }}:<br/>
                        <span v-for="hour in saturdayHours">
                            {{hour.open_time | moment("h:mm a", timezone)}} - {{hour.close_time | moment("h:mm a", timezone)}}    
                        </span>
                    </p>
                </div>
                <div>
                    <p>
                        {{ $t("hours.hours-sun") }}:<br/>  
                        <span v-for="hour in sundayHours">
                            {{hour.open_time | moment("h:mm a", timezone)}} - {{hour.close_time | moment("h:mm a", timezone)}}    
                        </span>
                    </p>
                </div>
            </div>
            <!--<div class="stores_container">-->
            <!--    <router-link tag="h3" to="/stores" exact>-->
            <!--        <a>{{ $t("hours.stores-title") }}</a>-->
            <!--    </router-link>-->
            <!--</div>-->
            <div class="page_container">
                <h1>{{ getPageName() }}</h1>
            </div>
        </div>
    </div>
</template>

<script>
    define(["Vue", "vuex"], function (Vue, Vuex) {
        return Vue.component("inside-header-component", {
            template: template, // the variable template will be injected,
            data: function () {
                return { }
            },
            computed: {
                ...Vuex.mapGetters([
                    'property',
                    'timezone',
                    'getPropertyHours'
                ]),
                weekdayHours() {
                    return _.filter(this.getPropertyHours, function(o) { return o.day_of_week == 1 });
                },
                saturdayHours() {
                    return _.filter(this.getPropertyHours, function(o) { return o.day_of_week == 6 });
                },
                sundayHours() {
                    return _.filter(this.getPropertyHours, function(o) { return o.day_of_week == 0 });
                }
            },
            methods: {
                getPageName(){
                    if(this.$route.fullPath == "/pages/cambridge-parties") {
                        return "Parties"
                    } else if(this.$route.fullPath == "/pages/cambridge-public-skating") {
                        return "Public Skating"
                    } else if(this.$route.fullPath == "/pages/cambridge-shinny-hockey") {
                        return "Shinny Hockey"
                    } else if(this.$route.fullPath == "/pages/cambridge-figure-skating") {
                        return "Figure Skating"
                    } else if(this.$route.fullPath == "/pages/cambridge-leagues") {
                        return "Leagues"
                    } else if(this.$route.fullPath == "/pages/cambridge-lessons") {
                        return "Lessons"
                    } else if(this.$route.fullPath == "/pages/cambridge-hockey-loft") {
                        return "Hockey Loft"
                    } else if(this.$route.fullPath == "/pages/cambridge-cancellations") {
                        return "Cancellations"
                    } else if(this.$route.fullPath == "/pages/cambridge-accessibility") {
                        return "Accessibility"
                    } else if(this.$route.fullPath == "/pages/cambridge-rental-availability") {
                        return "Rental Availability"
                    } else if(this.$route.fullPath == "/pages/cambridge-advertising") {
                        return "Advertising"
                    } else if(this.$route.fullPath == "/pages/cambridge-privacy-policy") {
                        return "Privacy Policy"
                    } else if(this.$route.fullPath == "/pages/cambridge-terms-conditions") {
                        return "Terms & Conditions"
                    } else if(this.$route.fullPath == "/pages/cambridge-contact-us") {
                        return "Contact Us"
                    } else {
                        return this.$route.meta.pageName     
                    }
                }    
            }
        });
    });
</script>