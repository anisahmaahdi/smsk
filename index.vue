<template>
  <div class="container">
    <link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css" />
    <h1 class="text-dark text-center">Surat Masuk</h1>
    <NuxtLink to="/tambah" class="btn btn-primary mb-3">Tambah</NuxtLink>
    <table border="2" width="50%">
      <thead class="w3-container w3-green">
        <tr>
          <th>No</th>
          <th>Tanggal</th>
          <th>Nomor Surat</th>
          <th>Dari</th>
          <th>Tujuan</th>
          <th>Perihal</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(visitor, i) in datas" :key="visitor.id">
          <td>{{ i + 1 }}</td>

          <td>{{ visitor.tanggal }}</td>
          <td>{{ visitor.nomorsurat }}</td>
          <td>{{ visitor.dari }}</td>
          <td>{{ visitor.tujuan }}</td>
          <td>{{ visitor.perihal }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
const supa = useSupabaseAuthClient();
const supabase = useSupabaseClient();
const datas = ref([]);

async function getData() {
  const { data, error } = await supa.from("pengunjung").select();
  datas.value = data;
  console.log(datas.value);
}

onMounted(() => {
  getData();
});
</script>
<style>
.p {
  margin-right: 10px;
}
</style>
