##node-influx writePoints write multiple points

<pre><code>
	let point = [
		{
			measurement: "test",
			tags: { marketName: "measurementA" },
			fields: {
				id: 94023954,
				price: "0.0027641",
				amount: "228733.1234",
				type: "buy"
			},
			timestamp: 1538121064186291 //务必带上时间戳才可成功写入
		},
		{
			measurement: "measurementA",
			tags: { marketName: "ABC" },
			fields: {
				id: 94023952,
				price: "0.0027641",
				amount: "33283.3244",
				type: "buy"
			},
			timestamp: 1538121064186291 //务必带上时间戳才可成功写入
		}
	];

	influx_trade_update.writePoints(point).then(() => {
		console.log("写入成功");
	});
</code></pre>