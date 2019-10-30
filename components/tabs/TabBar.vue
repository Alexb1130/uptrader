<script>
import TabContent from "@/components/tabs/TabContent";
export default {
    components: {
        TabContent
    },
	data() {
		return {
			tabsTitles: ["Торговать", "Инвестировать", "Привлекать инвесторов"],
			tabActive: 0
		};
	}
};
</script>

<template>
	<section class="tabs">
		<div class="tab-bar">
			<div class="container">
				<ul class="tab-bar__list">
					<li v-for="(title, i) in tabsTitles" :key="i">
						<button
							@click="tabActive = i"
							:class="{ active: tabActive === i }"
							class="subtitle"
						>
							{{ title }}
						</button>
					</li>
				</ul>
			</div>
		</div>
        <div class="container">
            <tab-content></tab-content>
        </div>
	</section>
</template>
<style lang="scss" scoped>
.tabs {
	min-height: 100vh;
	background-color: #eac7aa;
	background: url("~assets/img/bg-2.jpg") center no-repeat;
	background-size: cover;
}
.tab-bar {
    border-bottom: 1px solid #e6e6e6;
    margin-bottom: 60px;

	&__list {
		padding: 0;
		display: flex;
		justify-content: center;
		li {
			flex: 1 1 0;
			list-style: none;
		}
		button {
			width: 100%;
			padding: 30px;
			border: 0;
			text-align: center;
			background: transparent;
            border-bottom: 2px solid transparent;
            transition: all .25s;
            cursor: pointer;

            @media (max-width: 1200px) {
                padding: 30px 15px;
                font-size: 23px;
            }

            &:focus {
                outline: 0;
                opacity: .8;
            }

			&.active {
				color: #009e82;
				border-color: #009e82;
			}
		}
	}
}
</style>
