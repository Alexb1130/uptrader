<script>
import TabContent from "@/components/tabs/TabContent";
export default {
	components: {
		TabContent
	},
	methods: {
		accordionToggle(evt) {
			evt.target.classList.toggle("active");
			evt.target.classList.contains("active")
				? (this.isActive = true)
				: (this.isActive = false);
		}
	},
	data() {
		return {
			items: [
				{
					title: "Торговать",
					icon: "icon-1.png",
					width: 35,
					height: 28
				},
				{
					title: "Инвестировать",
					icon: "icon-2.png",
					width: 35,
					height: 28
				},
				{
					title: "Привлекать инвесторов",
					icon: "icon-3.png",
					width: 30,
					height: 38
				}
			],
			isActive: false
		};
	}
};
</script>
<template>
	<section class="accordion" :class="{ active: isActive }">
		<div class="container">
			<h1 class="title">
				Выберите способ заработка
			</h1>
			<ul class="accordion__list">
				<li
					class="accordion__list-item"
					v-for="(item, i) in items"
					:key="i"
				>
					<button @click.prevent="accordionToggle" class="subtitle">
						<img
							:width="item.width"
							:height="item.height"
							:src="require(`~/assets/img/${item.icon}`)"
							alt=""
						/>
						{{ item.title }}
						<img
							class="arrow"
							src="~assets/img/arrow.svg"
							alt="arrow"
						/>
					</button>
					<tab-content>
					</tab-content>
				</li>
			</ul>
		</div>
	</section>
</template>
<style lang="scss" scoped>
.accordion {
	position: relative;
	display: flex;
	flex-direction: column;
	min-height: 100vh;
	background-color: #eac7aa;
	background: url("~assets/img/bg-1.jpg") center no-repeat;
	background-size: cover;

	&.active {
		background: url("~assets/img/bg-2.jpg") bottom no-repeat;
		background-size: contain;
	}

	.container {
		margin: unset;
	}

	.tab-content {
		margin-top: 30px;
		display: none;
	}

	&__list {
		padding: 0;
	}
	&__list-item {
		list-style: none;
		margin-bottom: 20px;
		button {
			width: 100%;
			padding: 30px 15px;
			display: flex;
			align-items: center;
			cursor: pointer;
			border: 0;
			border-radius: 3px;
			background-color: rgba(#ffffff, 0.5);
			transition: all 0.25s;

			&.active {
				& + .tab-content {
					display: block;
				}

				.arrow {
					transform: rotate(180deg);
				}
			}
		}
		img {
			margin-right: 10px;
		}
	}
}

.arrow {
	margin-left: auto;
	transform-origin: center;
	transition: all 0.25s;
}
</style>
