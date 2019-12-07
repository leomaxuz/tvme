<template>
  <q-page class="q-pa-md">
    <q-list bordered>
      <q-item 
	    v-for="task in tasks"
		:key="task.id"
		@click="task.completed = !task.completed"
		clickable
		v-ripple>
        <q-item-section side top>
          <q-checkbox v-model="task.completed" />
        </q-item-section>
        
		<q-item-section >
          <q-item-label>{{ task.name }}</q-item-label>
        </q-item-section>
		
		<q-item-section side top>
		  <q-icon name="event" />
          <q-item-label caption>{{ task.dueDate }}</q-item-label>
          <q-item-label caption>
		   <small>{{ task.dueTime }}</small>
		  </q-item-label>
        </q-item-section>
		
      </q-item>

    </q-list>
  </q-page>
</template>

<script>
export default {
	data() {
		return {
			tasks:[
				{
					id:1,
					name:'Go to shop',
					completed:false,
					dueDate:'2019/08/10',
					dueTime:'18:30'
				},
				{
					id:2,
					name:'Get banners',
					completed:false,
					dueDate:'2019/08/11',
					dueTime:'18:30'				},
				{
					id:3,
					name:'Get apples',
					completed:false,
					dueDate:'2019/08/12',
					dueTime:'18:30'
				}
			]
		}
	}
}
</script>
