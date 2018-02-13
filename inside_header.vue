<template>
    <div class="inside_header_background">
        <div class="main_container">
            <div class="hours_container">
                <h3>{{ $t("hours.hours-title") }}</h3>
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
            <div class="stores_container">
                <router-link tag="h3" to="/stores" exact>
                    <a>{{ $t("hours.stores-title") }}</a>
                </router-link>
            </div>
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
                    } else {
                        return this.$route.meta.pageName     
                    }
                }    
            }
        });
    });
</script>