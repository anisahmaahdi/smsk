<template>
  <div class="thead" style="display: block">
    <h1>Surat Masuk</h1>
    <form @submit.prevent="simpan">
      <!-- <input v-model="nomorsurat" placeholder="nomor surat" /> <br /> -->
      <input v-model="nomorsurat" plachedor="nomorsurat" /> <br />
      <input v-model="dari" placeholder="dari" /> <br />
      <input v-model="tujuan" placeholder="tujuan" /> <br />
      <input v-model="perihal" placeholder="perihal" /> <br />

      <button type="submit">kirim</button>
    </form>
  </div>
</template>

<script setup>
const supabase = useSupabaseAuthClient();

// const nomorsurat = ref();
const nomorsurat = ref();
const dari = ref();
const tujuan = ref();
const perihal = ref();

async function simpan() {
  const { data, error } = await supabase.from("pengunjung").insert({
    nomorsurat: nomorsurat.value,
    dari: dari.value,
    tujuan: tujuan.value,
    perihal: perihal.value,
    // jenis: jenis.value,
  });
  navigateTo("/");
  if (error) {
    console.log(error);
  }
}
</script>

<style scoped>
thead {
  background-color: rgb(34, 11, 151);
}
tbody {
  background-color: rgb(218, 20, 20);
}
</style>
