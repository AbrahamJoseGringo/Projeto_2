<script setup>

const produtos = [
    {
        id: 1,
        nome: 'Camiseta',
        preco: 49.90
    },
    {
        id: 2,
        nome: 'Calça',
        preco: 99.90
    },
    {
        id: 3,
        nome: 'Meia',
        preco: 9.90
    },
    {
        id: 4,
        nome: 'Sapato',
        preco: 199.90
    },
    {
        id: 5,
        nome: 'Boné',
        preco: 29.90
    },
    {
        id: 6,
        nome: 'Óculos',
        preco: 99.90
    },
    {
        id: 7,
        nome: 'Relógio',
        preco: 299.90
    },
    {
        id: 8,
        nome: 'Bermuda',
        preco: 79.90
    },
    {
        id: 9,
        nome: 'Cueca',
        preco: 19.90
    },
    {
        id: 10,
        nome: 'Meia',
        preco: 9.90
    }
]

</script>
<template>
  <ul>
    <li v-for="item in produtos" :key="item.id">
      <p>{{ item.nome }}</p> 
      
      
    </li>
  </ul>
  <ul>
    <li v-for="item in produtos" :key="item.id">
      
      <p>R${{ item.preco}} </p> 
      
    </li>
  </ul>
</template>
<style>
ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px;
  border: 1px solid #ccc;
  border-radius: 8px;
  margin-bottom: 8px;
}

li p {
  margin: 0;
}

li p:first-of-type {
  font-weight: bold;
}

li p:last-of-type {
  color: #007bff;
}
</style>