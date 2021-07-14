<template>
  <div class="title">Why Is Mace Mad At Elris Today?</div>
    <div>
        <img v-show="runGif" src="@/assets/DOS_Morgenstern.gif">
        <img v-show="!runGif" src="@/assets/still_img.png">
    </div>
    <div id="reason" class="reason" v-if="showReason"> 
      <div v-bind:class="{flip: flipClass}" v-on:animationend="removeAnimation">{{ reason }}</div>
    </div>
  <button id="reroll" v-if="showButton" @click="getNewReason">{{ buttonText }}</button>
</template>

<script>
export default {
    data () {
        return {
            showReason: false,
            reason: null,
            listOfReasons: [
                'Elris threw him again.',
                'STOP THROWING ME ELRIS!',
                'Sassith got the last kill.',
                'Torvaris got the last kill.',
                'Briley got the last kill.',
                'Fautha got the last kill.',
                'Drix got the last kill',
                'Drix brought up Limp Bizkit again',
                'Some enemy is still alive.',
                'Some innocent bystander is still alive.',
                'A conversation didn\'t lead to murder.',
                'A conversation lead to murder, but he didn\'t get to do it.',
                'A conversation lead to murder, but it took too long to get there.',
                'Elris used eldtrich blast at point blank.',
                'Elris used hellish rebuke at point blank.',
                'Elris healed someone instead of killing them. WTF man?',
                'Elris was attacked and didn\'t retaliate.',
                'Elris was attacked and retaliated, but didn\'t use Mace to do it.',
                'Fautha said he smelled funny.',
                'The cleric is glowing again. Weirdo.',
                'The party took too long looting rather than killing things.',
                'There\'s nothing around to kill.',
                'There\'s something around to kill but it\'s not dead yet. WHY NOT?!',
                'Elris said something to Mace rather than killing something with Mace.',
                'Something died due to magic rather than Mace\'s blunt force trauma.',
                'Because "The Decider" is having more fun than me right now.'
            ],
            buttonText: 'Find Out',
            flipClass: false,
            runGif: false,
            showButton: true,
        }
    },
    methods: {
        removeAnimation: function () {
            this.flipClass  = false;
            this.runGif = false;
            this.showButton = true;

        },
        getNewReason: function () {
            let chosenReason = Math.floor(Math.random() * this.listOfReasons.length);
            this.reason = this.listOfReasons[chosenReason];
            this.runGif = true; 
            this.showReason = false; 
            this.showButton = false;
            setTimeout(() => {
                this.showReason = true;
                this.buttonText = 'That can\'t be it';
                this.flipClass = true;
            }, 650);
            
        },
        
    },
}
</script>

<style scoped>
    .title {
        color: rgb(241, 241, 241);
        font-family: 'Lato', sans-serif;
        font-size: 42px;
        margin-top: 175px;
        margin-bottom: 85px;
        padding: 50px auto;
        text-align: center;
        letter-spacing: 1px;
    }
    button {
        border-radius: 10px;
        border: 1px;
        font-size: 28px;
        color: rgb(65, 65, 65);
        margin-top: 75px;
        cursor: pointer;
    }
    button:hover{
        background-color: rgb(200, 200, 200);
    }
    .reason {
        font-size: 36px;
        font-weight: 100;
        color: #eee;
        height: 65px;
        padding-top: 10px;
        margin: 0 auto;  
        margin-top: 10px;
    }
    .flip { animation: flip 1.5s }
    @keyframes flip {
    0% { margin-top: -50px; }
    50% { margin-top: 75px;}
    100% { margin-top: 0px; }
}

</style>