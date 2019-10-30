<script>
export default {
	data() {
		return {
			items: [
				{
					title: "Торговать",
					icon: "icon-1.png"
				},
				{
					title: "Инвестировать",
					icon: "icon-2.png"
				},
				{
					title: "Привлекать инвесторов",
					icon: "icon-3.png"
				}
			]
		};
    },
    props: {
        onClick: {
            type: Function
        }
    }
};
</script>

<template>
	<section class="features-list">
		<div class="container">
			<div class="features-list__inner">
				<h1 class="title">
					Выберите способ заработка
				</h1>
				<ul class="list">
					<li class="list__item" v-for="(item, i) in items" :key="i">
						<button class="subtitle" @click.prevent="onClick">
							<img
								:src="require(`~/assets/img/${item.icon}`)"
								alt=""
							/>
							{{ item.title }}
						</button>
					</li>
				</ul>
			</div>
		</div>
	</section>
</template>

<style lang="scss" scoped>
.features-list {
	display: flex;
	justify-content: center;
	align-items: center;
	min-height: 100vh;
	background-color: #eac7aa;
	background: url("~assets/img/bg-1.jpg") center no-repeat;
	background-size: cover;
}
.list {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    padding: 0;
	&__item {
        list-style: none;
		button {
            position: relative;
            margin: 15px;
            width: 365px;
            height: 365px;
            display: flex;
            flex-direction: column;
			justify-content: center;
			align-items: center;
            cursor: pointer;
            border: 0;
			border-radius: 50%;
            background-color: rgba(#ffffff, 0.5);
            transition: all .25s;

            &:hover::before,
            &:focus::before {
                opacity: 1;
            }
            &:focus {
                outline: 0;
            }

            &::before {
                content: '';
                position: absolute;
                width: 95%;
                height: 95%;
                border-radius: 50%;
                border: 2px solid #69cbc3;
                opacity: 0;
                transition: inherit;
            }
        }
        img {
            margin-bottom: 40px;
        }
	}
}
</style>
