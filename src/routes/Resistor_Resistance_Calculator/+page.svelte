<script>
	let band1;
	let band2;
	let band3;
	let band4;
	let resistanceResult = '';

	function calculate_resistance() {
		let band1_int = parseInt(band1);
		let band2_int = parseInt(band2);
		let band3_int = parseInt(band3);
		let band4_int = parseFloat(band4);
		let resistance = (band1_int * 10 + band2_int) * Math.pow(10, band3_int);
		resistanceResult = resistance.toString() + ' ohms';
		console.log(band4_int);

		if (band4_int != 0) {
			let band4_percentage = band4_int / 100;
			let band4_value = resistance * band4_percentage;
			let band4_value_rounded = Math.round(band4_value * 100) / 100;
			resistanceResult = resistanceResult + ' ± ' + band4_value_rounded.toString() + ' ohms';
		} else {
			resistanceResult = resistanceResult + ' ± 0 ohms';
		}
	}

	const value_to_colour = {
		0: '#141412',
		1: '#744418',
		2: '#A71717',
		3: '#D4770D',
		4: '#D6D600',
		5: '#206916',
		6: '#0E1A63',
		7: '#5B106E',
		8: '#797979',
		9: '#FAFAFA'
	};

	const band4_value_to_colour = {
		0: '#d9bb7a',
		1: '#744418',
		2: '#A71717',
		0.5: '#206916',
		0.25: '#0E1A63',
		0.1: '#5B106E',
		0.05: '#797979',
		5: '#FFD700',
		10: '#FAFAFA'
	};
</script>

<div id="main-div">
	<div class="band-select">
		<div>
			<label for="band1" class="label">Band 1</label>
			<select
				id="select-band1"
				style="background-color: {value_to_colour[band1]}"
				name="band1"
				class="select"
				bind:value={band1}
			>
				<option value="0" style="background-color: #141412; color: white;">Black</option>
				<option value="1" style="background-color: #744418; color: white;">Brown</option>
				<option value="2" style="background-color: #A71717; color: white;">Red</option>
				<option value="3" style="background-color: #D4770D; color: white;">Orange</option>
				<option value="4" style="background-color: #D6D600; color: white;">Yellow</option>
				<option value="5" style="background-color: #206916; color: white;">Green</option>
				<option value="6" style="background-color: #0E1A63; color: white;">Blue</option>
				<option value="7" style="background-color: #5B106E; color: white;">Violet</option>
				<option value="8" style="background-color: #797979; color: white;">Grey</option>
				<option value="9" style="background-color: #FAFAFA; color: black;">White</option>
			</select>
		</div>
		<div>
			<label for="band2" class="label">Band 2</label>
			<select
				id="select-band2"
				style="background-color: {value_to_colour[band2]}"
				name="band2"
				class="select"
				bind:value={band2}
			>
				<option value="0" style="background-color: #141412; color: white;">Black</option>
				<option value="1" style="background-color: #744418; color: white;">Brown</option>
				<option value="2" style="background-color: #A71717; color: white;">Red</option>
				<option value="3" style="background-color: #D4770D; color: white;">Orange</option>
				<option value="4" style="background-color: #D6D600; color: white;">Yellow</option>
				<option value="5" style="background-color: #206916; color: white;">Green</option>
				<option value="6" style="background-color: #0E1A63; color: white;">Blue</option>
				<option value="7" style="background-color: #5B106E; color: white;">Violet</option>
				<option value="8" style="background-color: #797979; color: white;">Grey</option>
				<option value="9" style="background-color: #FAFAFA; color: black;">White</option>
			</select>
		</div>
		<div>
			<label for="band3" class="label">Band 3</label>
			<select
				id="select-band3"
				style="background-color: {value_to_colour[band3]}"
				name="band3"
				class="select"
				bind:value={band3}
			>
				<option value="0" style="background-color: #141412; color: white;">Black</option>
				<option value="1" style="background-color: #744418; color: white;">Brown</option>
				<option value="2" style="background-color: #A71717; color: white;">Red</option>
				<option value="3" style="background-color: #D4770D; color: white;">Orange</option>
				<option value="4" style="background-color: #D6D600; color: white;">Yellow</option>
				<option value="5" style="background-color: #206916; color: white;">Green</option>
				<option value="6" style="background-color: #0E1A63; color: white;">Blue</option>
				<option value="7" style="background-color: #5B106E; color: white;">Violet</option>
				<option value="8" style="background-color: #797979; color: white;">Grey</option>
				<option value="9" style="background-color: #FAFAFA; color: black;">White</option>
			</select>
		</div>
		<div>
			<label for="band4" class="label">Band 4</label>
			<select
				id="select-band4"
				style="background-color: {band4_value_to_colour[band4]}"
				name="band4"
				class="select"
				bind:value={band4}
			>
				<option value="0" style="background-color: #F3F3F3; color: black;">None</option>
				<option value="1" style="background-color: #744418; color: white;">Brown</option>
				<option value="2" style="background-color: #A71717; color: white;">Red</option>
				<option value="0.5" style="background-color: #206916; color: white;">Green</option>
				<option value="0.25" style="background-color: #0E1A63; color: white;">Blue</option>
				<option value="0.1" style="background-color: #5B106E; color: white;">Violet</option>
				<option value="0.05" style="background-color: #797979; color: white;">Grey</option>
				<option value="5" style="background-color: #FFD700; color: white;">Gold</option>
				<option value="10" style="background-color: #FAFAFA; color: black;">White</option>
			</select>
		</div>
	</div>
	<div class="band-info-display">
		<p id="band1-info-display">Band 1: {band1}</p>
		<p id="band2-info-display">Band 2: {band2 * 10}</p>
		<p id="band3-info-display">Band 3: {band3}</p>
		<p id="band4-info-display">Band 4: ±{band4}%</p>
	</div>
	<div>
		<button on:click={calculate_resistance}>Calculate</button>
	</div>
	<p>Resistance: {resistanceResult}</p>

	<!-- SVG -->
	<div class="resistor-div">
		<!-- svelte-ignore illegal-attribute-character -->
		<svg width="21600" height="1080" id="resistor">
			<defs id="defs4" />

			<sodipodi:namedview
				id="base"
				pagecolor="#ffffff"
				bordercolor="#666666"
				borderopacity="1.0"
				inkscape:pageopacity="0.0"
				inkscape:pageshadow="2"
				inkscape:zoom="0.12374369"
				inkscape:cx="504.15002"
				inkscape:cy="205.80139"
				inkscape:document-units="in"
				inkscape:current-layer="layer1"
				showgrid="false"
				units="in"
				inkscape:window-width="1366"
				inkscape:window-height="721"
				inkscape:window-x="-4"
				inkscape:window-y="-4"
				inkscape:window-maximized="1"
			/>
			<metadata id="metadata7">
				<rdf:RDF>
					<cc:Work rdf:about="">
						<dc:format>image/svg+xml</dc:format>
						<dc:type rdf:resource="http://purl.org/dc/dcmitype/StillImage" />
						<dc:title></dc:title>
					</cc:Work>
				</rdf:RDF>
			</metadata>
			<g
				inkscape:label="Layer 1"
				inkscape:groupmode="layer"
				id="layer1"
				transform="translate(0,27.6403), scale(0.2)"
			>
				<g id="g3825">
					<rect
						y="318.11612"
						x="32.324883"
						height="48.487324"
						width="2080.9143"
						id="rect3004"
						style="fill:#666666;stroke:none"
					/>
					<path
						inkscape:connector-curvature="0"
						id="rect3776"
						transform="translate(0,-1107.6403)"
						d="m 798.5625,1308.5625 c -21.47944,0 -37.32619,4.0094 -49.46875,10.5625 -0.0526,0.028 -0.10377,0.065 -0.15625,0.094 -18.04664,8.9915 -27.35769,22.7119 -33.90625,37.4374 -14.51122,27.7533 -22.11341,59.0945 -55.8125,69.0938 -1.31397,0.3899 -2.62206,0.7469 -3.9375,1.125 l 0,46.2188 c 1.31639,0.3788 2.62251,0.766 3.9375,1.1562 64.74738,19.2121 12.93753,117.1875 139.34375,117.1875 0.73556,0 1.52761,-0.033 2.3125,-0.062 1.42733,0.029 2.86724,0.062 4.34375,0.062 30.2139,0 103.1066,-25.625 131.1875,-25.625 l 185.24995,0 c 28.081,0 100.9736,25.625 131.1876,25.625 1.4764,0 2.9164,-0.034 4.3437,-0.062 0.7849,0.03 1.5769,0.062 2.3125,0.062 126.4062,0 74.5964,-97.9754 139.3438,-117.1875 1.3149,-0.3902 2.6211,-0.7774 3.9374,-1.1562 l 0,-46.2188 c -1.3154,-0.3781 -2.6235,-0.7351 -3.9374,-1.125 -33.6993,-9.9993 -41.3013,-41.3405 -55.8126,-69.0938 -6.5485,-14.7255 -15.8596,-28.4459 -33.9062,-37.4374 -0.053,-0.029 -0.1037,-0.065 -0.1562,-0.094 -12.1426,-6.5531 -27.9894,-10.5625 -49.4688,-10.5625 -0.7233,0 -1.4833,0.034 -2.25,0.062 -1.4474,-0.029 -2.9088,-0.062 -4.4062,-0.062 -30.214,0 -103.1066,25.625 -131.1876,25.625 l -185.24995,0 c -28.0809,0 -100.9736,-25.625 -131.1875,-25.625 -1.49753,0 -2.95885,0.034 -4.40625,0.062 -0.76674,-0.029 -1.52669,-0.062 -2.25,-0.062 z"
						style="fill:#d9bb7a;fill-opacity:1;stroke:#565248"
					/>
					<path
						id="rect3796"
						transform="translate(0,-27.6403)"
						d="M 798.5625 228.5625 C 794.83997 228.5625 791.30046 228.67303 787.90625 228.90625 L 787.90625 511.1875 C 791.31332 511.35148 794.85648 511.4375 798.5625 511.4375 C 799.29806 511.4375 800.09011 511.404 800.875 511.375 C 802.30233 511.404 803.74224 511.4375 805.21875 511.4375 C 817.35302 511.4375 836.39057 507.29016 856.625 502.34375 L 856.625 237.65625 C 836.39057 232.70984 817.35302 228.5625 805.21875 228.5625 C 803.72122 228.5625 802.2599 228.597 800.8125 228.625 C 800.04576 228.596 799.28581 228.5625 798.5625 228.5625 z "
						style="fill:{value_to_colour[band1]};fill-opacity:1;"
					/>
					<path
						id="rect3798"
						transform="translate(0,-27.6403)"
						d="M 901.0625 248.5625 L 901.0625 491.4375 C 915.3171 488.17202 927.92103 485.8125 936.40625 485.8125 L 969.75 485.8125 L 969.75 254.1875 L 936.40625 254.1875 C 927.92103 254.1875 915.3171 251.82798 901.0625 248.5625 z "
						style="fill:{value_to_colour[
							band2
						]};fill-opacity:1;stroke-width:0.99000000000000021;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1"
					/>
					<path
						id="rect3800"
						transform="translate(0,-27.6403)"
						d="M 1014.1875 254.1875 L 1014.1875 485.8125 L 1082.875 485.8125 L 1082.875 254.1875 L 1014.1875 254.1875 z "
						style="fill:{value_to_colour[band3]};fill-opacity:1;"
					/>
					<path
						id="rect3819"
						transform="translate(0,-27.6403)"
						d="M 1252.8438 228.5625 C 1246.3558 228.5625 1237.9014 229.76927 1228.3438 231.625 L 1228.3438 508.375 C 1237.9014 510.23073 1246.3558 511.4375 1252.8438 511.4375 C 1254.3202 511.4375 1255.7602 511.403 1257.1875 511.375 C 1257.9724 511.405 1258.7644 511.4375 1259.5 511.4375 C 1274.3045 511.4375 1286.6423 510.09139 1297.0312 507.6875 L 1297.0312 234 C 1286.8423 230.56088 1274.5655 228.5625 1259.5 228.5625 C 1258.7767 228.5625 1258.0167 228.597 1257.25 228.625 C 1255.8026 228.596 1254.3411 228.5625 1252.8438 228.5625 z "
						style="fill:{band4_value_to_colour[band4]};fill-opacity:1;stroke:none"
					/>
				</g>
			</g>
		</svg>
	</div>
</div>

<style>
	/* div {
		outline: 1px red solid;
	} */

	#main-div {
		display: flex;
		flex-direction: column;
		justify-content: center;
	}

	.band-select {
		display: flex;
		flex-direction: row;
		margin-bottom: 20px;
		justify-content: space-around;
	}

	.label {
		margin-bottom: 5px;
	}

	.select {
		margin-bottom: 10px;
		padding: 8px;
		background-color: #333;
		color: white;
		border: none;
		border-radius: 2px;
	}
	.resistor-div {
		/* outline: 5px solid red; */
		display: flex;
    justify-content: center;
    align-items: center;
	}
	#select-band4 {
		/* background-color: {band4_value_to_colour[band4]}; */
	}

	.select option {
		background-color: #333;
		color: white;
	}

	button {
		padding: 10px;
		background-color: #131d13;
		color: white;
		border: none;
		border-radius: 4px;
		cursor: pointer;
	}

	button:hover {
		background-color: #45a049;
	}

	p {
		margin-bottom: 10px;
	}

	.band-info-display {
		display: flex;
		flex-direction: row;
		justify-content: space-around;
	}
	:global(body) {
		background-color: #1c2333;
		font-family: Verdana, Geneva, Tahoma, sans-serif;
		font-size: 16px;
		color: #d7def3;
	}
</style>
