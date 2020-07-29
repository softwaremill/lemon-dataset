![](docs/img/logo.png)

# Lemons quality control dataset :lemon:
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![version](https://img.shields.io/badge/version-1.0.0-yellow.svg)](https://semver.org)

Lemon dataset has been prepared to investigate the possibilities to tackle the issue of fruit quality control. It contains 2690 annotated images (1056 x 1056 pixels). Raw lemon images have been captured using the procedure described in the following [blogpost](https://blog.softwaremill.com/when-life-gives-you-lemons-create-a-dataset-70522d6b1aa0) and manually annotated using [CVAT](https://github.com/opencv/cvat).

Here's an example of raw unannotated data:

![](docs/img/lemon-dataset-raw-sprite.png)

and some annotated samples:

![](docs/img/lemon-dataset-annotated-sprite.png)

## Labels

| Name               | Attribute       | Type             | Default | Description                                                                                                                                                                                                            | Example                                                                                                        |
| ---                | ---             | ---              | ---     | ---                                                                                                                                                                                                                    | ---                                                                                                            |
| condition          | healthy         | boolean          | true    | Determine whether the fruit is healthy. If not regions with identified issues are annotated                                                                                                                             | ![](docs/img/examples/healthy.png)                                                                             |
| condition          | greening        | boolean          | false   | Determine whether the fruit contains areas that are not uniformly yellow and have green areas.                                                                                                                         | ![](docs/img/examples/greening.png)                                                                            |
| image_quality      | blurry          | boolean          | false   | Fruit image is blurry                                                                                                                                                                                                  | ![](docs/img/examples/blurry.png)                                                                              |
| image_quality      | cropped         | boolean          | false   | Not all fruit parts are on the image                                                                                                                                                                                   | ![](docs/img/examples/cropped.png)                                                                             |
| image_quality      | unnatural_color | boolean          | false   | There are issues with color representation.                                                                                                                                                                            | ![](docs/img/examples/unnatural_color.png)                                                                     |
| image_quality      | no_data         | boolean          | false   | There are black spots on the fruit image that do not contain data.                                                                                                                                                     | ![](docs/img/examples/no_data.png)                                                                             |
| illness            | -               | region           | -       | -                                                                                                                                                                                                                      | ![](docs/img/examples/illness_1.png) ![](docs/img/examples/illness_2.png) ![](docs/img/examples/illness_3.png) |
| gangrene           | -               | region           | -       | -                                                                                                                                                                                                                      | ![](docs/img/examples/gangrene.png)                                                                            |
| mould              | -               | region           | -       | -                                                                                                                                                                                                                      | ![](docs/img/examples/mould.png)                                                                               |
| blemish            | artificial      | region + boolean | -       | -                                                                                                                                                                                                                      | ![](docs/img/examples/blemish_1.png) ![](docs/img/examples/blemish_2.png)                                      |
| dark_style_remains | -               | region           | -       | After pollination the remains of style are preserved in the fruit. A dark area around the remain of style indicates an unhealthy fruit. This place is the region from which the fruit starts rotting or catches mould. | ![](docs/img/examples/dark_style_remains_1.png) ![](docs/img/examples/dark_style_remains_2.png)                |
| pedicel            | -               | region           | -       | Pedicel refers to a structure connecting a single flower to its inflorescence.                                                                                                                                         | ![](docs/img/examples/pedicel.png)                                                                             |
| artifact           | -               | region           | -       | Image contains artifacts i.e. regions that are not related to a fruit and are a result of wrong image processing. Those regions should be identified and described.                                                    | ![](docs/img/examples/artifact.png)                                                                            |

## File name

You will notice that file names are composed to form a specific identifier e.g.:
`0037_G_I_120_A`: `0037` (individual fruit instance), `120` (relative photo angle), `A` (photo position). Some of them are restricted to the original project and cannot be published.

## Download data

| File                                    | Format | Version |
| ---                                     | ---    | ---     |
| [Lemon Dataset](data/lemon-dataset.zip) | COCO   | v1      |

[COCO API](https://github.com/cocodataset/cocoapi) can be utilized to read the dataset.

```python
from pycocotools.coco import COCO

coco = COCO('../lemon-dataset/annotations/instances_default.json')
```

## Citing
If you use the lemons data set in a scientific publication, we would appreciate references to the following paper:

Biblatex entry:
```latex
@misc{softwaremill_2020,
  author       = {Maciej Adamiak},
  title        = {Lemons quality control dataset},
  institution  = {SoftwareMill},
  month        = jul,
  year         = 2020,
  note         = {https://github.com/softwaremill/lemon-dataset},
  doi          = {???},
  url          = {https://doi.org/???}
}
```

## License

MIT License

Copyright (c) 2020 SoftwareMill

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.