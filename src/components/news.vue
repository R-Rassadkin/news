<template>
<div class="task">
    <p class="p">{{name}}</p>
        <app-button 
        @action="open" 
        color="BtnOpen" 
        >{{isNewsOpen?'Закрыть':'Открыть'}}</app-button>

        <app-button
        color='BtnDanger' 
        @action="$emit('unmark',id)"
        v-if="wasRead" 
        >отметить непрочитанной</app-button>

    <div class="solution" v-if="isNewsOpen">
        <hr>
        <p class="title">{{title}}</p>
        <app-button 
            color="BtnRead" 
            v-if="!wasRead" 
            @action="mark"
            >отметить прочитанной</app-button>
    </div>
</div>
</template>
<script>
import AppButton from './AppButton'

export default {
    emits:{
        'open-news':null,
        'read-news'(id){
            if (id) {
                return true
            }
            console.warn('нет параметра id для emits news-read');
            return false
        },
        'unmark':null
    },
    props:{
        title:{
        type:String,
        required:true
        },
        id:{
            type:Number,
            required:true
        },
        name:{
            type:String,
            required:true
        },
        wasRead:{
            type:Boolean,
            required:true
        },
        isOpen:{
            type:Boolean,
            required:true
        }
    },
    data() {
        return {
            isNewsOpen:this.isOpen,
            newsRead:this.wasRead
        }
    },
    methods:{
        open(){
            this.isNewsOpen=!this.isNewsOpen
            if (this.isNewsOpen) {
                this.$emit('open-news')
            }
            
            
        },
        mark(){
                this.isNewsOpen=false
                this.$emit('read-news',this.id)
        }
        
        
    },
    components:{
         AppButton 
    }
}
</script>
<style scoped>
.task{
    height: auto;
    margin: 0 auto;
    width: 1700px;
    background-color: rgb(233, 250, 231);
    border:2px solid rgb(3, 12, 3);
    margin-top: 50px;
    padding: 30px;
    border-radius: 20px;
    position: relative;
}
.p{
    font-size: 25px;
    width: 400px;
    margin-left: 700px;
    color: rgb(52, 104, 0);

}
.solution{
    font-size: 25px;
    margin: 0 auto;
    margin-top: 10px;
    margin-bottom: 20px;
    height: 100px;
    width: 1000px;
} 
.title{
    margin-left: 100px;
    color: brown;
    position: relative;
    left: 10px;
}
.BtnOpen{
    height: 35px;
    width: 150px;
    background-color: rgb(249, 250, 249);
    color: rgb(24, 54, 23);
    border:2px solid rgb(24, 117, 21);
    font-size: 20px;
    border-radius: 20px;
    margin-left: 1500px;
    outline: none;
    position: absolute;
    left: 50px;
    top: 40px;
    
}
.BtnOpen:hover{
    border:3px solid rgb(35, 129, 26);
    background-color: rgb(243, 250, 188);
    color: rgb(8, 100, 5);
    font-size: 23px;
}
.BtnRead{
    height: 35px;
    width: 250px;
    border:1px solid black;
    font-size: 20px;
    border-radius: 20px;
    background-color: rgb(42, 110, 74);
    color:  rgb(254, 255, 255);
    border:3px solid rgb(52, 136, 101);
    outline: none;
    position: absolute;
    bottom: 100px;
    left: 1450px;
}
.BtnRead:hover{
    border:3px solid rgb(11, 98, 3);
    background-color: rgb(243, 250, 188);
    color: rgb(8, 100, 5);
    font-weight: 600;
}
.BtnDanger{
    
    width: 300px;
    border:2px solid rgb(36, 1, 1);
    font-size: 20px;
    border-radius: 20px;
    background-color: rgb(221, 86, 86);
    color: white;
    margin-right: 10px;
    right: 200px;
    left: 1300px;
    outline: none;
    position: absolute;
    left: 1200px;
    top: 43px;
}
.BtnDanger:hover{
    color: rgb(255, 253, 253);
    background-color: rgb(216, 100, 100);
    border:3px solid rgb(90, 4, 4);
    font-weight: 600;

}
</style>