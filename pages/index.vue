<script>
import FeaturesList from "@/components/features/List";
import TabBar from "@/components/tabs/TabBar";
import Accordion from "@/components/accordion/Accordion";
export default {
	components: {
        FeaturesList,
        TabBar,
        Accordion
	},
	data() {
		return {
			window: {
				width: 0,
				height: 0
            },
            desctop: 790,
			show: false
		};
	},
	mounted() {
		if (process.browser) {
			window.addEventListener("resize", this.handleResize);
			this.handleResize();
		}
	},
	methods: {
		handleResize() {
			this.window.width = window.innerWidth;
			this.window.height = window.innerHeight;
		},
		renderTabs() {
			this.show = !this.show;
		}
	}
};
</script>
<template>
	<div v-if="window.width >= desctop">
		<transition name="fade-out">
			<features-list v-if="!show" :onClick="renderTabs" />
		</transition>
		<transition name="fade-in">
			<tab-bar v-if="show"></tab-bar>
		</transition>
	</div>
    <div v-else>
        <accordion />
    </div>
</template>
<style scoped>
.fade-out-enter-active,
.fade-out-leave-active {
	transition: all 0.7s;
}
.fade-out-enter,
.fade-out-leave-to {
	transform: translateY(-100px);
	opacity: 0;
}

.fade-in-enter-active,
.fade-in-leave-active {
	transition: all 1.5s;
}
.fade-in-enter,
.fade-in-leave-to {
    transform: translateY(100px);
}
</style>
