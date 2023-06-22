<template>
  <div id="burger-table" v-if="burgers">
    <div>
      <div id="burger-table-heading">
        <div class="order-id">#:</div>
        <div>Customer:</div>
        <div>Bread:</div>
        <div>Meat:</div>
        <div>Optionals:</div>
        <div>Actions:</div>
      </div>
    </div>
    <div id="burger-table-rows">
      <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
        <div class="order-number">{{ burger.id }}</div>
        <div>{{ burger.nome }}</div>
        <div>{{ burger.pao }}</div>
        <div>{{ burger.carne }}</div>
        <div>
          <ul v-for="(opcional, index) in burger.opcionais" :key="index">
            <li>{{ opcional }}</li>
          </ul>
        </div>
        <div class="burger-table-row-btns">
          <select
            name="status"
            class="status"
            @change="updateBurger($event, burger.id)"
          >
            <option
              :value="s.tipo"
              v-for="s in status"
              :key="s.id"
              :selected="burger.status == s.tipo"
            >
              {{ s.tipo }}
            </option>
          </select>
          <button class="delete-btn" @click="deleteBurger(burger.id)">
            Delete
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Dashboard",
  data() {
    return {
      burgers: null,
      burger_id: null,
      status: [],
    };
  },
  methods: {
    async getPedidos() {
      const req = await fetch("http://localhost:3000/burgers");

      const data = await req.json();

      this.burgers = data;

      // Resgata os status de pedidos
      this.getStatus();
    },
    async getStatus() {
      const req = await fetch("http://localhost:3000/status");

      const data = await req.json();

      this.status = data;
    },
    async deleteBurger(id) {
      const req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "DELETE",
      });

      const res = await req.json();

      this.getPedidos();
    },
    async updateBurger(event, id) {
      const option = event.target.value;

      const dataJson = JSON.stringify({ status: option });

      const req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "PATCH",
        headers: { "Content-Type": "application/json" },
        body: dataJson,
      });

      const res = await req.json();

      console.log(res);
    },
  },
  mounted() {
    this.getPedidos();
  },
};
</script>

<style scoped>
#burger-table {
  max-width: 1200px;
  margin: 0 auto;
}

#burger-table-heading,
#burger-table-rows,
.burger-table-row {
  display: flex;
  flex-wrap: wrap;
}

#burger-table-heading {
  font-weight: bold;
  padding: 12px;
  border-bottom: 3px solid #333;
}

.burger-table-row {
  width: 100%;
  padding: 12px;
  border-bottom: 1px solid #ccc;
}

#burger-table-heading div,
.burger-table-row div {
  width: 19%;
}

#burger-table-heading .order-id,
.burger-table-row .order-number {
  width: 5%;
}

select {
  padding: 12px 6px;
  margin-right: 12px;
}

.delete-btn {
  background-color: #000000;
  color: #fbcb31;
  font-weight: bold;
  border: 2px solid #000000;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
}

.delete-btn:hover {
  background-color: transparent;
  color: #000000;
}

@media only screen and (max-width: 790px) {
  #burger-table {
    width: 569px;
    overflow: scroll;
  }

  .burger-table-row div ul {
    list-style: none;
  }

  .burger-table-row-btns {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .burger-table-row-btns select {
    margin-bottom: 10px;
  }
}
</style>
