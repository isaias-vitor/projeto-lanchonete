<template>

    <div>
        <div class="alert alert-success" role="alert">
            {{ msg }}
        </div>
    </div>
    
</template>

<script>
export default{
    name: 'Messagem',
    props:{
        msg: String
    }
}
</script>