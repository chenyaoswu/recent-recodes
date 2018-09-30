## node-influx writePoints write multiple points（node-influex写入多条数据）

Tips:  多条数据写入需要添加时间戳，且时间戳精确到纳秒，需补充到19位，如不够长，直接追加0到19位即可

<pre><code>
	let point = [
		const influx = new Influx.InfluxDB({
			host: '', //  外网
			database: '',
			port: 8086,
			schema: [
				{
				measurement: 'measurement',
				fields: {
					a: Influx.FieldType.FLOAT,
					b: Influx.FieldType.FLOAT,
					c: Influx.FieldType.FLOAT,
				},
				tags: [
					'tags_a',
				],
				},
			],
			});
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
			tags: { tags_a: "ABC" },
			fields: {
				a: 94023952,
				b: "0.0027641",
				c: "33283.3244",
			},
			timestamp: 1538121064186293 //务必带上时间戳才可成功写入
		}
	];

	influx.writePoints(point).then(() => {
		console.log("写入成功");
	});
</code></pre>