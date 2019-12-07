<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          icon="menu"
          aria-label="Menu"
        />

        <q-toolbar-title>
          Quasar App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>
	
	<q-footer>
	  <q-tabs>
	    <q-tab 
			v-for="nav in navs"
			:to="nav.to"
			:icon="nav.icon" 
			:label="nav.label"
			exact>
		</q-tab>
	  </q-tabs>
	</q-footer>
	
    <q-drawer
      v-model="leftDrawerOpen"
      bordered
      content-class="bg-grey-2">
      <q-list>
        <q-item-label header>Navigation</q-item-label>
        
		<q-item 
			v-for="nav in navs"
			:to="nav.to"
			exact
			clickable>
          <q-item-section avatar>
            <q-icon :name="nav.icon" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{ nav.label }}</q-item-label>
          </q-item-section>
        </q-item>
		      
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
	import { openURL } from 'quasar'

	export default {
		name: 'MyLayout',
		data () {
			return {
				leftDrawerOpen: this.$q.platform.is.desktop,
				navs: [
					{label:'List',icon:'list',to: '/'},
					{label:'Settings',icon:'settings',to:'/settings'}
				]
			}
		},
		methods: { openURL }
	}
</script>
