<template>
  <div class="container h-screen mx-auto p-4 bg-gray-50 ">
    <div class="bg-white p-6 rounded-lg shadow-md max-w-6xl mx-auto">
      <h1 class="text-3xl font-bold text-center mb-5">To do List </h1>
      <div class="mb-4">
        <div class="flex items-center gap-4 mb-2">
          <div class="flex items-center gap-2">
            <label for="start" class="font-semibold text-lg">Start:</label>
            <input type="time" id="start" v-model="startTime" class="border border-gray-300 rounded p-2 "/>
          </div>
          <div class="flex items-center gap-2">
            <label for="end" class="font-semibold text-lg">End:</label>
            <input type="time" id="end" v-model="endTime" class="border border-gray-300 rounded p-2"/>
          </div>
          <div class="flex items-center gap-2">
            <label for="date" class="font-semibold text-lg">Date</label>
            <input type="date" id="date" v-model="date" class="border border-gray-300 rounded p-2"/>
          </div>
          <input type="text" placeholder="Activity" v-model="activity" class="border border-gray-300 rounded-lg p-2 w-full text-center focus:border-black focus:shadow-outline"/>
          <button @click="addTodo" class="bg-black text-white px-6 py-2 rounded hover:bg-gray-600">
            Add
          </button>
        </div>
      </div>
      <div class=" mx-auto mb-5">
        <div v-for="(item, index) in todoList" :key="index" class="flex items-center gap-4 bg-white p-4 border-b border-gray-300">
          <button @click="deleteItem(index)" class="bg-red-800 text-sm text-white px-3 py-2 rounded hover:bg-red-600">
            Delete
          </button>
          <button @click="done(index)" class="bg-green-600 text-sm text-white px-3 py-2 rounded hover:bg-green-400">
            Done
          </button>
          <span :class="{'line-through text-red-500': item.status}">{{ item.start }} to {{ item.end }} - {{ item.text }} | Date {{ item.date }}</span>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      todoList: [
        {text: "Feat: Import testrun to docx", start: '14-00', end: '16-00', date:'08/07/2024', status: false},
        {text: "Feat: Bulk import data to database", start: '16-00', end: '18-00', date:'08/07/2024', status: false},
        {text: "Belajar VueJS", start: '18-00', end: '19-00', date:'08/07/2024', status: false},
        {text: "Belajar CSS", start: '19-00', end: '20-00', date:'08/07/2024', status: false},
        {text: "Buat relasi kategori blog app", start: '21-00', end: '22-00', date:'08/07/2024', status: false},
        {text: "fix bug kiwi-report", start: '23-00', end: '24-00', date:'08/07/2024', status: false},
      ],
      startTime: '',
      endTime: '',
      date: '',
      activity: ''
    };
  },
  methods: {
    addTodo(){
      const newItem = {
        text: this.activity,
        start: this.startTime, 
        end: this.endTime,
        date: this.date,
        status: false
      }

      this.todoList.push(newItem)
    },
    deleteItem(index){
      this.todoList.splice(index, 1)
    },
    done(index){
      this.todoList[index].status = !this.todoList[index].status;
    }
  },
}
</script>

