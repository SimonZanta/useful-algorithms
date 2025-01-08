# useful-algorithms
repository of useful algorithms
## linear interpolation for timestamps
- useful when having for eg. two different sized datasets and i want to see values from both of them

``` js
linearInterpolate(dataset: Point[], common_timestamps: number[]): number[] {
		const n = dataset.length;
		const interpolated: number[] = [];
    for (let t of common_timestamps) {
			let interpolated_value = 0;
       // Check if the timestamp falls within the dataset range
			if (t < dataset[0].x || t > dataset[n - 1].x) {
				// if not set zero
				interpolated_value = 0;
			} else {
				// Find the segment where the timestamp falls
				for (let i = 0; i < n - 1; i++) {
					if (dataset[i].x <= t && t <= dataset[i + 1].x) {
						const x1 = dataset[i].x;
						const y1 = dataset[i].y;
						const x2 = dataset[i + 1].x;
						const y2 = dataset[i + 1].y;
            //Linear interpolation
						const fraction = (t - x1) / (x2 - x1);
						interpolated_value = Math.round(y1 + fraction * (y2 - y1));
						//exit loop after found value
						break;
					}
				}
			}
			interpolated.push(interpolated_value);
		}
    return interpolated;
} 
```
