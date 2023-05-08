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

export default {
    const carrinho= []:
  data() {
    return {
     carrinho: {
        items: [],
        total: 0
      },
      produtos
  }
  methods: {
    adicionarProduto(produtos) {
      const itemCarrinho = this.carrinho.items.find(item => item.id === produtos.id);
     
      if (itemCarrinho) {
        itemCarrinho.quantidade++;
        itemCarrinho.valorTotal = itemCarrinho.preco * itemCarrinho.quantidade;
      } 
      else {
        const novoItem = {
          produtos,
          quantidade: 1,
          valorTotal: produtos.preco
        };
        this.carrinho.items.push(novoItem);
      }

      this.carrinho.total += produto.preco;
    }
    incrementarQuantidade(index) {
      const item = this.carrinho.items[index];
      item.quantidade++;
      item.valorTotal = item.preco * item.quantidade;
      this.carrinho.total += item.preco;
    },
    decrement(item) {
      const index = this.carrinho.items.findIndex(i => i.id === item.id);

      if (this.carrinho.items[index].quantidade > 1) {
        this.carrinho.items[index].quantidade--;
        this.carrinho.items[index].valorTotal = this.carrinho.items[index].preco * this.carrinho.items[index].quantidade;
        this.carrinho.total -= this.carrinho.items[index].preco;
      } else {
        this.remove(item);
      }
    },
    remove(item) {
      const index = this.carrinho.items.findIndex(i => i.id === item.id);
      const quantidade = this.carrinho.items[index].quantidade;
      this.carrinho.items.splice(index, 1);
      this.carrinho.total -= item.preco * quantidade;
    }
  }
};

</script>
<template>
  <div>
    <h2>Produtos</h2>
    <ul>
      <li v-for="produto in produtos" :key="produto.id">
        {{ produto.nome }} - R$ {{ produto.preco.toFixed(2) }}
        <button @click="adicionarProduto(produto)">Adicionar ao carrinho</button>
      </li>
    </ul>

    <h2>Carrinho</h2>
    <ul>
      <li v-for="(item, index) in carrinho.items" :key="item.id">
        {{ item.nome }} - R$ {{ item.preco.toFixed(2) }}
        <button @click="removerProduto(index)">Remover</button>
        <div>
          Quantidade: {{ item.quantidade }}
          <button @click="incrementarQuantidade(index)">+</button>
          <button @click="decrementarQuantidade(index)">-</button>
        </div>
        <div>
          Valor total: R$ {{ item.valorTotal.toFixed(2) }}
        </div>
      </li>
    </ul>

    <div>
      <h3>Total: R$ {{ carrinho.total.toFixed(2) }}</h3>
    </div>
  </div>
</template>