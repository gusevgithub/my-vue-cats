<template>
	<div id='wrapper'>
		<h1>Ты сегодня покормил кота?</h1>
		<div class="wrapper-product" v-for="product in arrProducts" :key="product.id">
			<div v-if="product.status !== '0'">
				<div class="product-parent" @click="oneClick(product.id)"  @mouseleave="oneMouseLeave(product.id)" :class="product.name_class">	
					<div class="product-child">
						<div class="product-child-fone"></div>
						<span class="tale">{{ product.tale }}</span>
						<h2>{{ product.title_h2 }}</h2>
						<h3>{{ product.title_h3 }}</h3>
						<span class="portion">{{ product.portion }}</span>
						<span class="gift"><br>{{ product.gift }}</span>
						<img :src="product.image" class="cat">
						<div class="circle">
							<span class="num-circle">{{ product.num_circle }}</span>
							<span class="kg-circle">{{ product.kg_circle }}</span>
						</div>
					</div>
				</div>
				<div v-if="product.name_class !== 'product-parent-focus' && product.name_class !== 'product-parent-active'">	
					<p class="text-bottom">{{ product.text_bottom }}</p>
					<span @click="oneClick(product.id)" @mouseleave="oneMouseLeave(product.id)" class="buy">{{ product.text_buy }}</span>
				</div>
				<div v-else>
					<p class="text-bottom">{{ product.text_bottom_fine }}</p>
				</div>
			</div>
			<div v-else-if="product.status === '0'">	
				<div class="product-parent-status">
					<div class="product-child-status">
						<div class="product-child-fone"></div>
						<span class="tale">{{ product.tale }}</span>
						<h2>{{ product.title_h2 }}</h2>
						<h3>{{ product.title_h3 }}</h3>
						<span class="portion">{{ product.portion }}</span>
						<span class="gift"><br>{{ product.gift }}</span>
						<img :src="product.image" class="cat">
						<div class="circle">
							<span class="num-circle">{{ product.num_circle }}</span>
							<span class="kg-circle">{{ product.kg_circle }}</span>
						</div>
					</div>
				</div>
				<p class="text-bottom" style="color: rgb(233, 233, 92);">{{ product.text_bottom_not }}</p>
				<span class="buy" style="display: none;">{{ product.text_buy }}</span>
			</div>
		</div>
	</div>
</template>
<script>
export default {
	data () {
		return {
			arrProducts: [
					{ 
						id: 0,
						name_class: '',
						tale: "Сказочное заморское яство",
						title_h2: "Нямушка",
						title_h3: "c фуа-гра",
						portion: "10 порций",
						gift: "мышь в подарок",
						image: "images/cat.png",
						num_circle: "0,5",
						kg_circle: "кг",
						text_bottom: "Чего сидишь? Порадуй один котэ,",
						text_bottom_fine: "Головы щучьи с чесноком да свежайщая сёмгушка.",
						text_bottom_not: "Печалька, с щукой закончился.",
						text_buy: "купи",
						status: "1"
					},
					{
						id: 1,
						name_class: '',
						tale: "Сказочное заморское яство",
						title_h2: "Нямушка",
						title_h3: "c рыбой",
						portion: "40 порций",
						gift: "2 мыши в подарок",
						image: "images/cat.png",
						num_circle: "2",
						kg_circle: "кг",
						text_bottom: "Чего сидишь? Порадуй два котэ,",
						text_bottom_fine: "Головы карася с чесноком да свежайщая сёмгушка.",
						text_bottom_not: "Печалька, с карасем закончился.",
						text_buy: "купи",
						status: "1"
					},
					{
						id: 2,
						name_class: '',
						tale: "Сказочное заморское яство",
						title_h2: "Нямушка",
						title_h3: "c курой",
						portion: "100 порций",
						gift: "5 мышей в подарок, заказчик доволен",
						image: "images/cat.png",
						num_circle: "5",
						kg_circle: "кг",
						text_bottom: "Чего сидишь? Порадуй три котэ,",
						text_bottom_fine: "Головы сома с чесноком да свежайщая сёмгушка.",
						text_bottom_not: "Печалька, с курой закончился.",
						text_buy: "купи",
						status: "0"
					}
				]
			}
		},
		methods: {
			oneClick: function(index) {
				if(this.arrProducts[index].name_class === '') {
					this.arrProducts[index].name_class = 'one-class'
				}
				if(this.arrProducts[index].name_class === 'product-parent-focus') {
					this.arrProducts[index].name_class = 'product-parent-active'	
				}
			},
			oneMouseLeave: function(index) {
				if(this.arrProducts[index].name_class === 'one-class') {
					this.arrProducts[index].name_class = 'product-parent-focus'
				}
				if(this.arrProducts[index].name_class === 'product-parent-active') {
					this.arrProducts[index].name_class = ''
				}
			}
		}
	}
</script>