<template>
    <div v-if="currentMessage" class="message_background">
        <div class="main_container message_content">
            <!--<span> {{currentMessage.body }} </span>-->
            <span> {{ property.description }} </span> 
        </div>
    </div>
</template>

<script>
    define(["Vue", "vuex"], function(Vue, Vuex){
        return Vue.component("messages-component", {
            template: template, // the variable template will be injected
            computed: {
                ...Vuex.mapGetters([
                    'property'
                ])
            }
        })
    });
</script>

