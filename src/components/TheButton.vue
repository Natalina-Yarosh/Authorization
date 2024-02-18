<template>
    <button class="btn">Login</button>
</template>

<style scoped>
.btn{
    width: 100%;
    background-color: var(--btn-bg-color);
    border-radius: 8px;
    border: 1px solid var(--btn-bg-color);
    padding: 16px;
    color: var(--white-color);
    font-weight: 600;
    font-size: 15px;
    line-height: 1;
    cursor: pointer;
    transition: all .3s linear;
    @media(max-width:850px){
        font-size: 14px;
    }
    @media(max-width:767px){
        font-size: 16px;
        padding: 15px;
    }
}

.btn:hover{
    background-color: transparent;
    color: var(--btn-bg-color);
}

.btn__secondary {
    background-color: transparent;
    color: var(--btn-bg-color);
}

.btn__secondary:hover{
    background-color: var(--btn-bg-color);
    color: var(--white-color);
}
</style>