<script>
export default {
	data() {
		return {
            text: 'Если вы ищете пассивный доход и предпочитаете, чтобы деньги для вас зарабатывал тот, кто умеет это делать, тогда попробуйте ЛАММ. ЛАММ – это сервис копирования сделок успешных трейдеров. Доходность ни чем не ограничена!',
            listTitle: 'Как это работает',
			listContent: [
				"Вы выбираете управляющего из рейтинга по фильтру Options",
				"Подключаете свой счет к счету Управляющего",
				"На вашем счете начинается копирование сделок",
				"Обратите внимание, что вы не перечисляете свои деньги Управляющему. Все ваши средства остаются на Вашем счете.",
				"Вы можете подключиться к нескольким Управляющим одновременно.",
				"Вы можете отключиться от Управляющих в любой момент."
            ],
            btnText: 'Продолжить'
		};
	}
};
</script>
<template>
	<div class="tab-content">
		<p class="tab-content__text">
			{{ text }}
		</p>
		<h4 class="tab-content__title"> {{listTitle}} </h4>
		<ul class="tab-content__list">
			<li v-for="(item, i) in listContent" :key="i">
				<span>{{ i + 1 }}</span> {{ item }}
			</li>
		</ul>
		<button class="btn">{{btnText}}</button>
	</div>
</template>
<style lang="scss" scoped>
.tab-content {
	max-width: 50%;
    font-weight: 400;

    @media (max-width: 790px) {
        max-width: 100%;
    }

	&__text {
		margin-bottom: 30px;
	}
	&__title {
		font-size: 24px;
		margin-bottom: 30px;
	}
	&__list {
		padding: 0;
		margin-bottom: 40px;
		li {
			display: flex;
			align-items: center;
			list-style: none;
			margin-bottom: 20px;
			span {
				margin-right: 10px;
				font-size: 32px;
				color: #00b596;
			}
		}
	}
}
.btn {
	padding: 15px 30px;
	border: 0;
	border-radius: 3px;
	color: #fff;
	font-weight: 600;
	background-color: #009e82;
}
</style>
