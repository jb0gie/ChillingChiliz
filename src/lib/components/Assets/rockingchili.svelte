<!--
Auto-generated by: https://github.com/threlte/threlte/tree/main/packages/gltf
Command: npx @threlte/gltf@2.0.1 rockingchili.glb -s -T
-->

<script>
	import { Group } from 'three';
	import { T, forwardEventHandlers } from '@threlte/core';
	import { useGltf, useGltfAnimations } from '@threlte/extras';

	export const ref = new Group();

	const gltf = useGltf('/models/rockingchili-transformed.glb', { useDraco: true });
	export const { actions, mixer } = useGltfAnimations(gltf, ref);

	$: $actions['PerfectChiliBlink']?.play();
	$: $actions['RockingChair']?.play();
	$: $actions['RockingChairBalance']?.play();
	$: $actions['RockingChili']?.play();

	const component = forwardEventHandlers();
</script>

<T is={ref} dispose={false} {...$$restProps} bind:this={$component}>
	{#await gltf}
		<slot name="fallback" />
	{:then gltf}
		<T.Group name="SceneSetup">
			<T.Group name="RockingChili" position={[-30.69, 0.8, 19.36]} rotation={[0, Math.PI / 4, 0]}>
				<T.Mesh
					name="Rocking_Chair"
					castShadow
					receiveShadow
					geometry={gltf.nodes.Rocking_Chair.geometry}
					material={gltf.materials.wire_006135113}
					rotation={[-0.29, 0, 0]}
					scale={0.8}
					
				>
					<T.Group name="ArmaturePerfectChili" rotation={[0.02, 0, 0]} scale={1.25}>
						<T is={gltf.nodes.hips} />
						<T.SkinnedMesh
							name="PerfectChili"
							castShadow
							receiveShadow
							geometry={gltf.nodes.PerfectChili.geometry}
							material={gltf.materials['Perfect_Baked.002']}
							skeleton={gltf.nodes.PerfectChili.skeleton}
							morphTargetDictionary={gltf.nodes.PerfectChili.morphTargetDictionary}
							morphTargetInfluences={gltf.nodes.PerfectChili.morphTargetInfluences}
						/>
					</T.Group>
				</T.Mesh>
			</T.Group>
		</T.Group>
	{:catch error}
		<slot name="error" {error} />
	{/await}

	<slot {ref} />
</T>
