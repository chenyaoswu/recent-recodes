## node-influex写入多条数据
## node-influx writePoints write multiple points

Tips:  多条数据写入需要添加时间戳，切时间戳精确到纳秒，需补充到19位，如不够长，直接追加0到19位即可

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