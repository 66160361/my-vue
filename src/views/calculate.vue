<script setup>
import { ref } from 'vue';
const number = ref(0);
function add(number) {
  number.value++;
}
</script>

<template>
  <!-- ✅ โหลด Bootstrap และฟอนต์ -->
  <link
    href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.3.2/css/bootstrap.min.css"
    rel="stylesheet"
  />
  <link
    href="https://fonts.googleapis.com/css2?family=Prompt:ital,wght@1,400&display=swap"
    rel="stylesheet"
  />

  <!-- ✅ จัดให้อยู่ตรงกลางจอ -->
  <div class="container d-flex justify-content-center align-items-center vh-100">
    <div class="card shadow-lg border-0 rounded-4" style="width: 500px;">
      <div class="card-body bg-gradient-custom rounded-4">
        <h1 class="text-center text-black fw-bold mb-4">✨ Multiplication ✨</h1>

        <!-- ช่องกรอกตัวเลข -->
        <div class="d-flex justify-content-center mb-4">
          <div class="input-group input-group-lg w-75">
            <input
              type="number"
              class="form-control text-center"
              v-bind:value="number"
              @input="number = Number($event.target.value)"
            />
            <button class="btn btn-success" @click="add(number)">
              <i class="bi bi-plus-circle"></i> Add
            </button>
          </div>
        </div>

        <!-- ตารางสูตรคูณ -->
        <div class="card table-card border-0 shadow">
          <div class="card-header bg-info text-white text-center fs-4 fw-bold">
            ตารางสูตรคูณ {{ number }}
          </div>

          <div class="card-body bg-white text-center">
            <ul class="list-group list-group-flush">
              <li
                v-for="i in 12"
                :key="i"
                class="list-group-item fs-5 fw-semibold"
              >
                {{ number }} × {{ i }} = {{ number * i }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.bg-gradient-custom {
  background: linear-gradient(135deg, #a8edea, #dff6f0);
}
.list-group-item {
  border: none;
  background: transparent;
}
body {
  font-family: 'Prompt', sans-serif;
}
</style>
