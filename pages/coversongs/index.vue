<script setup lang="ts">
type Coversong = {
  title: string;
  artist: string;
  id: string;
};

const songsCsv = await queryContent('/coversongs/coversongs').findOne();
const songs: Coversong[] = songsCsv.body as unknown as Coversong[];
</script>

<template>
  <div class="container mx-auto">
    <h2>Coversongs</h2>

    <table class="w-full table-auto">
      <thead>
        <tr>
          <th>Title</th>
          <th>Artist</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="song of songs">
          <td>
            {{ song.title }}
          </td>
          <td>
            {{ song.artist }}
          </td>
          <td>
            <NuxtLink :to="`/coversongs/${song.id}`"> Sheet </NuxtLink>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped></style>
