<script setup>
    const props = defineProps(['setOperacaoSelecionada'])
</script>

<template>
    <form>
        <select class="form-control" @change="props.setOperacaoSelecionada">
            <option value="somar">Somar</option>
            <option value="subtrair">Subtrair</option>
            <option value="multiplicar">Multiplicar</option>
            <option value="divisao">Dividir</option>
        </select>
        <br>
    </form>
</template>