<script lang="ts">
	export let mood: 'happy' | 'content' | 'sad' | 'very-sad' | 'sleeping' = 'happy';
	export let isJumping: boolean = false;
	// export let isWaving: boolean = false;
	// export let isEating: boolean = false;
	export let isSleeping: boolean = false;

	$: displayMood = isSleeping ? 'sleeping' : mood;
</script>

<div class="relative h-64 w-64 select-none">
	<svg
		width={256}
		height={256}
		viewBox="0 0 300 300"
		fill="none"
		xmlns="http://www.w3.org/2000/svg"
	>
		<path
			d="M150 290C227.32 290 290 227.32 290 150C290 72.6801 227.32 10 150 10C72.6801 10 10 72.6801 10 150C10 227.32 72.6801 290 150 290Z"
			fill="url(#paint0_radial_2007_873)"
		/>
		<g clip-path="url(#clip0_2007_873)" class:animate-bounce={isJumping}>
			<path
				opacity="0.9"
				d="M210 230C218.837 230 226 225.523 226 220C226 214.477 218.837 210 210 210C201.163 210 194 214.477 194 220C194 225.523 201.163 230 210 230Z"
				fill="#C49A6C"
			/>
			<path
				d="M150 302C189.765 302 222 260.81 222 210C222 159.19 189.765 118 150 118C110.235 118 78 159.19 78 210C78 260.81 110.235 302 150 302Z"
				fill="#B98B5B"
			/>
			<path
				d="M150 298C182.033 298 208 263.078 208 220C208 176.922 182.033 142 150 142C117.967 142 92 176.922 92 220C92 263.078 117.967 298 150 298Z"
				fill="#E5D1B8"
			/>
			<path
				d="M150 210C183.137 210 210 183.137 210 150C210 116.863 183.137 90 150 90C116.863 90 90 116.863 90 150C90 183.137 116.863 210 150 210Z"
				fill="#B98B5B"
			/>
			<path
				d="M110 127C119.941 127 128 117.15 128 105C128 92.8497 119.941 83 110 83C100.059 83 92 92.8497 92 105C92 117.15 100.059 127 110 127Z"
				fill="#B98B5B"
			/>
			<path
				d="M190 127C199.941 127 208 117.15 208 105C208 92.8497 199.941 83 190 83C180.059 83 172 92.8497 172 105C172 117.15 180.059 127 190 127Z"
				fill="#B98B5B"
			/>
			<path
				d="M110 122C115.523 122 120 115.732 120 108C120 100.268 115.523 94 110 94C104.477 94 100 100.268 100 108C100 115.732 104.477 122 110 122Z"
				fill="#EBC2A8"
			/>
			<path
				d="M190 122C195.523 122 200 115.732 200 108C200 100.268 195.523 94 190 94C184.477 94 180 100.268 180 108C180 115.732 184.477 122 190 122Z"
				fill="#EBC2A8"
			/>
			<path
				d="M150 198C168.778 198 184 185.464 184 170C184 154.536 168.778 142 150 142C131.222 142 116 154.536 116 170C116 185.464 131.222 198 150 198Z"
				fill="#E5D1B8"
			/>
			{#if displayMood === 'sleeping'}
				<path
					d="M120 126C126.667 131.333 133.333 131.333 140 126"
					stroke="#111111"
					stroke-width="6"
					stroke-linecap="round"
				/>
				<path
					d="M160 126C166.667 131.333 173.333 131.333 180 126"
					stroke="#111111"
					stroke-width="6"
					stroke-linecap="round"
				/>
			{:else}
				<path
					d="M130 138C135.523 138 140 133.523 140 128C140 122.477 135.523 118 130 118C124.477 118 120 122.477 120 128C120 133.523 124.477 138 130 138Z"
					fill="#111111"
				/>
				<path
					d="M170 138C175.523 138 180 133.523 180 128C180 122.477 175.523 118 170 118C164.477 118 160 122.477 160 128C160 133.523 164.477 138 170 138Z"
					fill="#111111"
				/>
				<path
					d="M126 127C127.657 127 129 125.657 129 124C129 122.343 127.657 121 126 121C124.343 121 123 122.343 123 124C123 125.657 124.343 127 126 127Z"
					fill="white"
				/>
				<path
					d="M166 127C167.657 127 169 125.657 169 124C169 122.343 167.657 121 166 121C164.343 121 163 122.343 163 124C163 125.657 164.343 127 166 127Z"
					fill="white"
				/>
			{/if}
			<path
				d="M150 155C152.761 155 155 152.761 155 150C155 147.239 152.761 145 150 145C147.239 145 145 147.239 145 150C145 152.761 147.239 155 150 155Z"
				fill="#111111"
			/>
			{#if displayMood === 'happy'}
				<path
					d="M136 178C146 183.333 156 183.333 166 178"
					stroke="#111111"
					stroke-width="6"
					stroke-linecap="round"
				/>
			{:else if displayMood === 'content' || displayMood === 'sleeping'}
				<path d="M136 180H166" stroke="#111111" stroke-width="6" stroke-linecap="round" />
			{:else if displayMood === 'sad' || displayMood === 'very-sad'}
				<path
					d="M136 182C146 176.667 156 176.667 166 182"
					stroke="#111111"
					stroke-width="6"
					stroke-linecap="round"
				/>
			{/if}
			<path
				d="M106 233C111.523 233 116 224.941 116 215C116 205.059 111.523 197 106 197C100.477 197 96 205.059 96 215C96 224.941 100.477 233 106 233Z"
				fill="#B98B5B"
			/>
			<path
				d="M194 233C199.523 233 204 224.941 204 215C204 205.059 199.523 197 194 197C188.477 197 184 205.059 184 215C184 224.941 188.477 233 194 233Z"
				fill="#B98B5B"
			/>
			<path
				opacity="0.3"
				d="M106 236C109.314 236 112 233.314 112 230C112 226.686 109.314 224 106 224C102.686 224 100 226.686 100 230C100 233.314 102.686 236 106 236Z"
				fill="#603A1A"
			/>
			<path
				opacity="0.3"
				d="M194 236C197.314 236 200 233.314 200 230C200 226.686 197.314 224 194 224C190.686 224 188 226.686 188 230C188 233.314 190.686 236 194 236Z"
				fill="#603A1A"
			/>
		</g>
		<defs>
			<radialGradient
				id="paint0_radial_2007_873"
				cx="0"
				cy="0"
				r="1"
				gradientUnits="userSpaceOnUse"
				gradientTransform="translate(14010 11210) scale(19600)"
			>
				<stop stop-color="#FFE98A" />
				<stop offset="1" stop-color="#FFD59E" />
			</radialGradient>
			<clipPath id="clip0_2007_873">
				<rect width="300" height="300" fill="white" />
			</clipPath>
		</defs>
	</svg>
</div>
