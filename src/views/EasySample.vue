<script setup>
  import { ref } from 'vue';
  import EasyHeader from '@/components/EasyHeader.vue';
  import EasyCard from '@/components/EasyCard.vue';
  import EasyFooter from '@/components/EasyFooter.vue';

  const data = ref({
    title: '這是一張卡片',
    content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugit expedita ipsa delectus nihil minus vero, maiores labore fuga praesentium quam harum totam rem commodi quis. Molestiae reiciendis perspiciatis quo doloremque!',
    imgUrl: 'https://images.unsplash.com/photo-1564507004663-b6dfb3c824d5?q=80&w=574&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
  });

  // 1.執行 emitTitle 這個 emit 的資料接收
  // 2.並轉由父層函式 editTitle 處理後續流程
  const editTitle = (newTitle) => {
    console.log({newTitle});
    data.value.title = newTitle;    
  };

  const arrayCard = ref([
    {id: 1, title: '卡片標題1', content: 'Placeat amet nulla vitae excepturi autem quos accusantium nesciunt.', imgUrl: 'https://plus.unsplash.com/premium_photo-1712736395906-dd23bfe7f3b2?q=80&w=550&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'},
    {id: 2, title: '卡片標題2', content: 'Placeat amet nulla vitae excepturi autem quos accusantium nesciunt.', imgUrl: 'https://plus.unsplash.com/premium_photo-1712736395906-dd23bfe7f3b2?q=80&w=550&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'},
    {id: 3, title: '卡片標題3', content: 'Placeat amet nulla vitae excepturi autem quos accusantium nesciunt.', imgUrl: 'https://plus.unsplash.com/premium_photo-1712736395906-dd23bfe7f3b2?q=80&w=550&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'},
    {id: 4, title: '卡片標題4', content: 'Placeat amet nulla vitae excepturi autem quos accusantium nesciunt.', imgUrl: 'https://plus.unsplash.com/premium_photo-1712736395906-dd23bfe7f3b2?q=80&w=550&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'},
    {id: 5, title: '卡片標題5', content: 'Placeat amet nulla vitae excepturi autem quos accusantium nesciunt.', imgUrl: 'https://plus.unsplash.com/premium_photo-1712736395906-dd23bfe7f3b2?q=80&w=550&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'},
  ]);

  const addCart = (cardTitle) => {
    console.log({cardTitle})
  };
</script>
<template>
  <div class="container">
    <EasyHeader />
    <!-- <div class="col-4">
      <EasyCard :content="data" @emit-title="editTitle"/>
    </div> -->
    <div class="row g-4">
      <div class="col-4" v-for="card in arrayCard" :key="card.id">
        <EasyCard :cardContent="card" @emitTitle="addCart" />
      </div>
    </div>
    <EasyFooter/>
  </div>
</template>

