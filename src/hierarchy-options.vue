<template>
	<div class="field">
		<div class="type-label">
			Parent Field
		</div>
		<v-select v-model="optParentFieldWritable" show-deselect
		          item-value="field" item-text="name"
		          :items="relationFields"
		/>
	</div>
	<div class="field">
		<div class="type-label">
			Templated Title
		</div>
		<v-collection-field-template v-model="optTitleWritable" :collection="collection" />
	</div>
	<div class="field">
		<v-checkbox v-model="optAllowReorderWritable" label="Allow reorder" />
	</div>
</template>


<script lang="ts" setup>
import { useI18n } from 'vue-i18n';
const { t } = useI18n();
import { Field } from '@directus/types';
import {useSync} from "@directus/extensions-sdk";

const props = defineProps<{
	collection: string;
	icon?: string;
	parentField?: Field;
	optParentField: string
	optTitle: string,
	optAllowReorder: boolean,
	relationFields: Field[]
}>();

const emit = defineEmits<{
	(e: 'update:optTitle', optTitle: string): void;
	(e: 'update:optParentField', optParentField: string): void;
	(e: 'update:optAllowReorder', optAllowReorder: boolean): void;
}>();

const optTitleWritable = useSync(props, 'optTitle', emit);
const optParentFieldWritable = useSync(props, 'optParentField', emit);
const optAllowReorderWritable = useSync(props, 'optAllowReorder', emit);
</script>































<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
	inheritAttrs: false,
});
</script>
