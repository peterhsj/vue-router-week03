<script setup>
  import { ref, computed } from 'vue';
  import Menu from '@/components/Menu.vue';
  import SelectList from '@/components/SelectList.vue';
  import OrderList from '@/components/OrderList.vue';

  const data = ref([
    {
      "id": 1,
      "name": "珍珠奶茶",
      "description": "香濃奶茶搭配QQ珍珠",
      "price": 50
    },
    {
      "id": 2,
      "name": "冬瓜檸檬",
      "description": "清新冬瓜配上新鮮檸檬",
      "price": 45
    },
    {
      "id": 3,
      "name": "翡翠檸檬",
      "description": "綠茶與檸檬的完美結合",
      "price": 55
    },
    {
      "id": 4,
      "name": "四季春茶",
      "description": "香醇四季春茶，回甘無比",
      "price": 45
    },
    {
      "id": 5,
      "name": "阿薩姆奶茶",
      "description": "阿薩姆紅茶搭配香醇鮮奶",
      "price": 50
    },
    {
      "id": 6,
      "name": "檸檬冰茶",
      "description": "檸檬與冰茶的清新組合",
      "price": 45
    },
    {
      "id": 7,
      "name": "芒果綠茶",
      "description": "芒果與綠茶的獨特風味",
      "price": 55
    },
    {
      "id": 8,
      "name": "抹茶拿鐵",
      "description": "抹茶與鮮奶的絕配",
      "price": 60
    }
  ]);
  const note = ref(null);


  // 選擇商品
  const orders = ref([]);
  const selectedItem = (item) => {
    // 重複選取不能加入
    const index = orders.value.findIndex(obj => obj.id === item.id);
    if (index >= 0) return;

    const order = {
      id: item.id,
      name: item.name,
      description: item.description,
      price: item.price,
      quantity: 1,
    };
    order.total = order.quantity * order.price;
    orders.value.push(order);
    
  };

  // 商品數量結算金額
  const itemSum = (item) => {
    item.total = item.quantity * item.price;    
  }

  // 總價計算
  const totalcount = computed(() => {
    return orders.value.length > 0 ? orders.value.map(item => item.total)
      .reduce((acc, cur) => acc + cur, 0) : 0;
  });

  // 送出表單
  const orderList = ref({
    order: [],
    note: null,
    total: 0
  });

  const saveOrder = () => {
    orderList.value = {
      order: [...orders.value],
      note: note.value,
      total: totalcount.value,
    }
    orders.value = [];
    note.value = null;
  };

  // 取消選取
  const cancelSelector = (id) => {
    const index = orders.value.findIndex(item => item.id === id);
    orders.value.splice(index, 1);
  };
</script>
<template>
  <div id="root">
    <div class="container mt-5">
      <div class="row">
        <div class="col-md-4">
          <Menu :data="data" @selectedItem="selectedItem" />
        </div>
        <div v-if="orders.length === 0" class="col-md-8">
          <div class="alert alert-primary text-center" role="alert">
            請選擇商品
          </div>
        </div>
        <div v-else class="col-md-8">
          <SelectList :orders="orders" @cancelSelector="cancelSelector" @itemSum="itemSum" />          
          <div class="text-end mb-3">
            <h5>總計: <span>${{ totalcount }}</span></h5>
          </div>
          <textarea
            v-model="note"
            class="form-control mb-3"
            rows="3"
            placeholder="備註"
          ></textarea>
          <div class="text-end">
            <button class="btn btn-primary" @click="saveOrder">送出</button>
          </div>
        </div>
      </div>
      <hr />
      <div v-if="orderList.order.length > 0" class="row justify-content-center">
        <div class="col-8">
          <div class="card">
            <div class="card-body">
              <div class="card-title">
                <h5>訂單</h5>
                <OrderList :orderList="orderList" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>