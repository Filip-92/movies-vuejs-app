<template>
    <div class="card p-3 text-center mb-3 mt-2">
        <video 
            :src="videoUrl" 
            ref="videoPlayer" 
            autoplay 
            @animationstart="onStart()" 
            @loadedmetadata="logDuration()"
            @ended="onEnd()" 
            controls
        >
        </video>
    </div>
</template>

<script>
export default {
    name: 'MovieCard',
    data() { return { 
        videoUrl: require('@/assets/filmy/' + this.movie),
        alreadyRun: false,
        interval: null,
    }; },
    props: {
        movie: {
            type: String
        },
    },
    methods: {
    logDuration() {
        this.interval = setInterval(() => {
            console.log(this.movie + ' halfway there' + ' (' + this.convertDuration(this.$refs?.videoPlayer?.duration / 2) + 's)')
        }, ((this.$refs?.videoPlayer?.duration / 2)*1000))
        setTimeout(() => clearInterval(this.interval), 
        ((this.$refs?.videoPlayer?.duration / 2)*1000))
    },
    onStart() {
    console.log(this.movie + ' started')
    },
    onEnd: function () {
    console.log(this.movie + ' ended' + ' (' + this.convertDuration(this.$refs?.videoPlayer?.duration) + 's)')
    },
    convertDuration(duration) {
    var num = Number(duration) // The Number() only visualizes the type and is not needed
    var roundedString = num.toFixed(2);
    var rounded = Number(roundedString); // toFixed
    return rounded;
    },
  },
  unmounted: function(){
    clearInterval(this.interval)
  },
  beforeUnmount () {
    clearInterval(this.interval)
  },
};
</script>

<style scoped>
    video {
        animation: pop-in 1s ease;
        -webkit-animation: pop-in 1s ease;
    }
    @keyframes popout {
        from{transform:scale(0)}
        80%{transform:scale(1.2)}
        to{transform:scale(1)}
    }
    @keyframes pop-in {
        0% { opacity: 0; transform: scale(0.5); }
        100% { opacity: 1; transform: scale(1); }
        }
    @-webkit-keyframes popout {
    from{-webkit-transform:scale(0)}
    80%{-webkit-transform:scale(1.2)}
    to{-webkit-transform:scale(1)}
    }
    .card {
        background-color: black;
    }
</style>
