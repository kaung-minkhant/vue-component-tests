<template>
  <div class="container m-auto w-full">
    <div class="w-[20%] m-auto">
      <input
        type="text"
        class="flex h-10 w-full rounded-md border border-input bg-background px-3 py-2 text-sm ring-offset-background file:border-0 file:bg-transparent file:text-sm file:font-medium placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50"
        v-model="inputToSearch"
        placeholder="Type in device name.."
        @input="search"
      />
      <div
        :class="['border border-slate-400 rounded-lg mt-3 p-2 w-full shadow-sm overflow-y-scroll', `max-h-[${maxSuggestion * 50}px]` ]"
        v-if="matchingSearch.length !== 0"
      >
        <div
          class="cursor-pointer hover:bg-slate-400 p-2 border-t first:border-none rounded-sm"
          v-for="search in matchingSearch"
          :key="search[searchKey]"
          @click="() => select(search)"
        >
          {{ search[selectField] }}
        </div>
      </div>
    </div>
  </div>
</template>

<style></style>

<script>
export default {
  props: {
    searchList: Array,
    selectField: String,
    searchKey: String,
    maxSuggestion: Number,
  },
  emits: ['selected'],
  data() {
    return {
      inputToSearch: "",
      matchingSearch: [],
    };
  },
  methods: {
    search() {
      if (this.inputToSearch.length === 0) {
        this.matchingSearch = [];
        return;
      }
      const matchingSearch = this.searchList.filter((search) => {
        return search[this.selectField]
          .toLowerCase()
          .includes(this.inputToSearch.toLowerCase());
      });
      this.matchingSearch = matchingSearch;
    },
    select(search) {
      this.inputToSearch = search[this.selectField];
      this.matchingSearch = [];
      this.$emit('selected', search)
    },
  },
};
</script>
