<template>
    <button 
        :class='color' 
        @click="$emit('action')"
        ><slot/>
    </button>
</template>
<script>
export default {
    emits:['action'],
    props:{
        text:{
            type:String,
            required:true
        },
        color:{
        type:String,
        dafault:'',
            validator(value){
            return ['BtnOpen','BtnDanger','BtnRead'].includes(value)
            }
        }
    },
    
}
</script>
