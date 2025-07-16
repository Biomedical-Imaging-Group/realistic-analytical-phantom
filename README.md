# Realistic Analytical Phantoms for Parallel MRI

Simulation tools for the validation of MRI reconstruction software.

Written by [Matthieu Guerquin-Kern](mailto:guerquin-kern(AT)@crans(DOT).org) at the Biomedical Imaging Group (BIG), EPFL, Switzerland

<p><img src="misc/brain176.png" width="176"/><img src="misc/brain176-error.png" width="176"/></p>

## Outline

This package is a collection of Matlab functions that implement analytical multi-channel MRI simulations of realistic phantoms.

It should be useful for testing the validity of the numerical implementations of a parallel MRI forward model. It also provides a realistic setting that avoids the inverse crime situation which can often result in over-optimistic reconstruction performances.

To facilitate the design of new phantoms, graphical interface tools are provided. For purposes of adequate visualization, exporting to the popular vector graphics formats SVG 1.1 and PDF (via the PGF/Tikz LATEX package) is supported.

## Reference

M. Guerquin-Kern, L. Lejeune, K.P. Pruessmann, and M. Unser, "[Realistic Analytical Phantoms for Parallel Magnetic Resonance Imaging](https://hal.science/hal-01814155v1/)," IEEE Transactions on Medical Imaging, vol. 31, no. 3, pp. 626-636, March 2012.

## Software

### Requirements

The code was tested with Matlab 7.12 (R2011a). Please feel free to contact us if you get any trouble with other versions.
As some parts of the code use compiled executables, it might not be straightforward to run the code with GNU Octave, a free alternative to Matlab.

Some scripts require the [IRT toolbox](http://www.eecs.umich.edu/~fessler/irt/fessler.tgz) (TGZ archive, 14 MB in 2024) of Jeff Fessler for NUFFT routines. Install this toolbox in your matlab path.

- If you have a Unix-like operating system on a multi-core computer, you can use the POSIX-thread library to parallelize the computations. To do so,
    1. make sure this library is installed on your system such that Matlab's mex can find it;
    2. uncomment line 30 in [`myerfzparts_c.cpp`](misc/myerfzparts_c.cpp).
- If you do not care much about calculation speed or if you use windows, or if things just do not work, just comment line 30 in [`myerfzparts_c.cpp`](misc/myerfzparts_c.cpp).

### Download and install

Download the code [here](https://github.com/Biomedical-Imaging-Group/realistic-analytical-phantom/archive/refs/heads/main.zip) (~22 MB).

Add the folder and subfolders in your matlab path. Some C++ sources are distributed with the code. To compile them as MEX binaries, simply run `make` in matlab prompt (make sure that you have a compiler installed using the mex setup).

### Conditions of use

No conditions. This is public domain. See [LICENSE](LICENSE).

## Examples

To start with the code, you can run and look into [`demo.m`](demo.m). The files in the [`exp/`](exp/) folder reproduce the results presented in the paper.

## Related Works

Preliminary investigations have been conducted during two student projects achieved by Isik Karahanoğlu and Laurent Lejeune. A report on intermediate results was made at the ISBI 2010 conference.

Some functions of this package are used in an [other package](https://github.com/Biomedical-Imaging-Group/mri-reconstruction) oriented towards MRI simulation and reconstruction.

## Acknowledgements

- Jeff Fessler for [NUFFT](http://www.eecs.umich.edu/~fessler/irt) and fruitful discussions and comments during ISBI 2008 and 2010.
- Marcel Leutenegger for the implementation details of [ERFZ](https://documents.epfl.ch/users/l/le/leuteneg/www/MATLABToolbox/ErrorFunction.html).
- Bruno Luong for his efficient MEX implementation of [insidepoly](http://www.mathworks.com/matlabcentral/fileexchange/27840-2d-polygon-interior-detection).
- Matt Fig for the Matlab [npermutek](https://www.mathworks.com/matlabcentral/fileexchange/11462-n_permute_k) code.
