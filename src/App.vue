<template>
	<div>Component Works</div>
</template>

<script lang="ts">
import gql from 'graphql-tag';
import { defineComponent } from '@vue/composition-api';
import { useResult } from '@vue/apollo-composable';
import * as VueCompositionApi from '@vue/composition-api';
import * as VueApolloComposable from '@vue/apollo-composable';

export type Maybe<T> = T | null | undefined;
export type GetLoggedInUserQueryVariables = {};

export type GetLoggedInUserQuery = { __typename?: 'Query' } & {
	me?: {
		id: string;
	};
};
type ReactiveFunctionGetLoggedInUserQuery = () => GetLoggedInUserQueryVariables;
export const GetLoggedInUserDocument = gql`
	query GetLoggedInUser {
		me {
			id
		}
	}
`;
export function useGetLoggedInUserQuery(
	variables?: GetLoggedInUserQueryVariables | VueCompositionApi.Ref<GetLoggedInUserQueryVariables> | ReactiveFunctionGetLoggedInUserQuery,
	baseOptions?: VueApolloComposable.UseQueryOptions<GetLoggedInUserQuery, GetLoggedInUserQueryVariables>,
) {
	return VueApolloComposable.useQuery<GetLoggedInUserQuery, GetLoggedInUserQueryVariables>(GetLoggedInUserDocument, variables, baseOptions);
}

export default defineComponent({
	name: 'App',
	setup() {
		const { result } = useGetLoggedInUserQuery();

		const example = useResult(result, null, data => data.me);

		return {
			example,
		};
	},
});
</script>

<style lang="scss" scoped></style>
