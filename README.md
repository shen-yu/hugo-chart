# hugo-chart

[![Awesome](https://awesome.re/badge.svg)](https://github.com/budparr/awesome-hugo)

English | [中文说明](README_zh-CN.md)

## About

This is not a standalone theme. It is a [Hugo](https://gohugo.io) theme component providing a shortcode: `chart` to display [Chart.js](https://www.chartjs.org/) in your Hugo site. 

![Screenshot](screenshots/1.png)

## Usage

1. Add the `hugo-chart` as a submodule to be able to get upstream changes later `git submodule add https://github.com/Shen-Yu/hugo-chart.git themes/hugo-chart`
2. Add `hugo-chart` as the left-most element of the `theme` list variable in your site's or theme's configuration file `config.yaml` or `config.toml`. Example, with `config.yaml`:
    ```yaml
    theme: ["hugo-chart", "my-theme"]
    ```
    or, with `config.toml`,
    ```toml
    theme = ["hugo-chart", "my-theme"]
    ```
3. In your site, use the shortcode, this way:
    ```go
    {{< chart [width] [height] >}}
    // Chartjs options goes here
    {{< /chart >}}

    ```

    |  Name   | Type  | Default  | Description  |
    |  ----  | ----  | ----  | ----  |
    | width  | number | 100 | The width of chart, responsive in window (%).  |
    | height  | number | 300 | The height of chart (px). |
    
4. Note that Chartjs is responsive as default, in order for the above code to correctly resize the chart height, the `maintainAspectRatio` option must be set to `false`.

## Example

```go
{{< chart 90 200 >}}
{
    type: 'bar',
    data: {
        labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
        datasets: [{
            label: 'Bar Chart',
            data: [12, 19, 18, 16, 13, 14],
            backgroundColor: [
                'rgba(255, 99, 132, 0.2)',
                'rgba(54, 162, 235, 0.2)',
                'rgba(255, 206, 86, 0.2)',
                'rgba(75, 192, 192, 0.2)',
                'rgba(153, 102, 255, 0.2)',
                'rgba(255, 159, 64, 0.2)'
            ],
            borderColor: [
                'rgba(255, 99, 132, 1)',
                'rgba(54, 162, 235, 1)',
                'rgba(255, 206, 86, 1)',
                'rgba(75, 192, 192, 1)',
                'rgba(153, 102, 255, 1)',
                'rgba(255, 159, 64, 1)'
            ],
            borderWidth: 1
        }]
    },
    options: {
        maintainAspectRatio: false,
        scales: {
            yAxes: [{
                ticks: {
                    beginAtZero: true
                }
            }]
        }
    }
}
{{< /chart >}}
```

![Bar chart](screenshots/2.png)

## License

[hugo-chart](https://github.com/Shen-Yu/hugo-chart) by [Eric Shen](https://github.com/Shen-Yu) is under [GPL v3](https://github.com/Shen-Yu/hugo-chart/blob/master/LICENSE) license.

![visitors-count](https://visitor-badge.laobi.icu/badge?page_id=Shen-Yu.hugo-chart)
