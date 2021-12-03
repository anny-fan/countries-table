<template>
  <div class="container-lg">
    <table class="table">
      <thead>
        <th v-for="obj in config" :key="obj.key">{{ obj.title }}</th>
      </thead>
      <tbody>
        <tr v-for="(row, index) in data" :key="index">
          <td v-for="(obj, index) in config" :key="index">
            <img
              v-if="obj.type === 'img'"
              :src="row[obj.key]"
              alt=""
              width="40"
            />
            <span v-if="obj.type === 'text'">{{ row[obj.key] }}</span>
            <ol
              v-if="obj.type === 'list'"
              class="list-group list-group-numbered"
            >
              <li
                class="list-group-item"
                v-for="item in row[obj.key]"
                :key="item"
              >
                {{ item }}
              </li>
            </ol>
            <span v-if="obj.type === 'textArray'">{{ row[obj.key][0] }}</span>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: ["data", "config"],
  data: () => ({
    // countries: [],
  }),
};
</script>

<style scoped lang="scss">
th {
  white-space: nowrap;
  padding: 5px 10px;
}
</style>
