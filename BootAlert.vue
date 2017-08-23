<template>
     <transition appear name="fade" v-on:after-enter="hideMessage">
        <div v-if="show" class="alert" v-bind:class="classObject" v-bind:alert-dismissable="alertDismissable==''">
            <a v-if="alertDismissable==''" href="#" class="close" data-dismiss="alert" aria-label="close">&times;</a>
            <p v-html="message"></p>
        </div>
    </transition>
</template>

<style>
.fade-enter-active, .fade-leave-active {
  transition: opacity 1s
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0
}
</style>

<script>
export default {
    data: function() {
      return {
        show: true
      }
    },
    methods: {
        hideMessage: function (el) {
            if (this.shouldDisappear == true) {
                var self = this;
                setTimeout(function() {self.show = false}, self.displayTime)
            }   
        },
        
    },
    props: { 
        message: {
            type: String,
            required: true
        },
        type: {
            type: String,
            default: 'info'
        },
        alertDismissable: {
        },
        displayTime: {
            type: Number,
            default: 5000
        },
        shouldDisappear: {
            default: true
        }
    },
    computed: {
        classObject: function () {
            return {
                'alert-danger': this.type=='danger',
                'alert-success': this.type=='success',
                'alert-info': this.type=='info',
                'alert-warning': this.type=='warning'
            }
        }
    }
}
</script>
