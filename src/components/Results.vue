<template>

     <p> Reaction time: {{ score }} ms</p>
     <p :class="rank"> <span> {{ rank }} </span></p>

</template>

<script>
export default {
    props: ["score"],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if(this.score < 200) {
            this.rank = "Challenger"
        } else if(this.score < 250) {
            this.rank = "Diamond"
        } else if (this.score < 400) {
            this.rank = "Platinum"
        }else if (this.score < 500) {
            this.rank = "Gold"
        } else if (this.score < 600) {
            this.rank = "Silver"
        } else if (this.score < 700) {
            this.rank = "Bronze"
        } else {
            this.rank = "Trash"
        }
        
    }
}
</script>

<style>
p {
    font-size: 3rem
}
span {
    font-weight: bold;
}
.Challenger {
    color: greenyellow;
}
.Diamond {
     color: blue;
}
.Platinum {
    color: aqua;
}
.Gold {
    color:gold;
}
.Silver {
    color: silver;
}
.Bronze {
    color: coral;
}
.Trash {
    color: black;
}

</style>