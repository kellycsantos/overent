<template>
	
    <div :style="`background: url('${championBackground}') no-repeat center;`">
		<div class="flex items-center">
			<div class="w-8/12 flex flex-col justify-items-stretch">
				<h2 class="mb-8 text-2xl">{{ championFunction }}</h2>
				<h1 class="mb-8 text-5xl uppercase">{{ championName }}</h1>
				<p class="mb-8">{{ championDescription }}</p>
			</div>
			<div >
				<img :src="championImg" class="w-11/12" />
			</div>


    <div class="w-8/12">
      <div v-for="ability, index in championAbilities" :key="index"
          class="bg-black/10 m-2 rounded-md" >
				<div>
          <span class="flex items-center">
            <img :src="ability.displayIcon" class="w-8">
             {{ability.displayName}}
          </span>
          
          <span>
           
          <small class="text-xs">{{ability.description}}</small>
          </span>

        </div>
        </div>
			</div>
		</div>

		<div class="flex justify-center bg-black/20">
			<span
				class="p-2 flex flex-wrap justify-center items-center xg:flex-nowrap"
				v-for="(role, index) in roles"
				:key="index"
			>
				<img :src="role.displayIcon" class="w-10" />
				<span
					class="border-2 border-black rounded-md w-20 skew-x-12 cursor-pointer m-1"
					v-for="(champion, index) in champions"
					:key="index"
					v-show="champion.class == role.role"
					@click="teste(index)"
				>
					<img :src="champion.displayIcon" class="w-full" />
				</span>
			</span>
		</div>
	</div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import axios from "axios";

export default defineComponent({
	name: "ChampionsGallery",
	props: {
		msg: String,
	},
	data() {
		return {
      color: 'red',
			champions: [],
			roles: [],
			selecionado: "",
			championFunction: "",
			championName: "",
			championDescription: "",
			championImg: "",
      championAbilities: "",
      championBackground:""
		};
	},
	methods: {
		teste(index: string | number) {
			this.selecionado = index;
			this.championFunction = this.champions[index].class;
			this.championName = this.champions[index].displayName;
			this.championDescription = this.champions[index].description;
			this.championImg = this.champions[index].fullPortrait;
      this.championAbilities = this.champions[index].abilities
      this.championBackground = this.champions[index].background
		},
		// setChampion(index: any){

		// },
		getChampions(): void {
			axios
				.get("https://valorant-info-api.herokuapp.com/")
				.then((response) => {
					this.champions = response.data.data;
					console.log(response.data.data);
				});
		},
		getRoles() {
			axios
				.get("https://valorant-info-api.herokuapp.com/")
				.then((response) => {
					this.roles = response.data.roles;
					console.log(response.data.roles);
				});
		},
	},
	mounted() {
		this.getChampions();
		this.getRoles();
		console.log("montei ok?");
	},
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* .galeria{
  background: red;
  display: flex;
} */
h3 {
	margin: 40px 0 0;
}
ul {
	list-style-type: none;
	padding: 0;
}
li {
	display: inline-block;
	margin: 0 10px;
}
a {
	color: #42b983;
}
</style>
