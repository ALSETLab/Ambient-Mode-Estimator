# Template-PMU-App
This template, based on NI Labview's [Continuous Measurement and Logging](http://www.ni.com/product-documentation/14031/en/), was developed to help you develop PMU applications using [S3DK](https://github.com/ALSETLab/S3DK) to access real-time synchrophasor measurements.
It provides a simple framework where the data management and other common interactions are already implemented, where the developer can easily plug in his algorithm.

## Create your Own PMU App
You can use this template to create your own PMU application based on [S3DK](https://github.com/ALSETLab/S3DK).
Simply clone the project on your own computer to get started.

**NOTE**: The project includes a GIT submodule in its dependencies that you should be initiated upon cloning the repository.
Usually, you can tick a box in the advanced settings to do a **recursive** cloning of the repo (e.g. 'recurse submodules' in SourceTree)

## Functionalities implemented
The following functionalities are implemented in the template:

 1. Automated PMU data aquisition through the S3DK
 2. Configurable PMU data buffering for parallel algorithms
 3. User settings management
 4. User configurable error handling

## License
The modifications applied to the original template are distributed under an MIT License with the following copyright information:

Copyright (c) 2018 Maxime Baudette

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


The original NI LabVIEW Continuous Measurement and Logging template is subject to the following copyright:
Developed in LabVIEW, Copyright © 2017 National Instrument Corporation.  All Rights Reserved
See [NI's software license agreement](http://www.ni.com/pdf/legal/us/software_license_agreement.pdf)
