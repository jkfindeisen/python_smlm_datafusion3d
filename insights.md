# Insights gained during stripping down the Matlab code

## Where is the most time spent?

demo1 with 50 particles (scales quadractically with the number of particles)

- all2all takes ~90% of time
- in all2all, it's pairFitting3D, in there it's gmmreg_L23D, in there it's gmmreg_l2_costfunc, in there it's .. mex_gausstransform
- one2all (called twice) ~5% of the time

## How to produce a binary release package?

Name: smlm_datafusion3d_matlab_minimal_win_1.0

Recipe:
- Build figtree with CMake (requires Matlab)
- Copy output to build/figtree-mex
- Build the main project with CMake (requires CUB, CUDA SDK and Matlab)
- Copy output to build/mex
- Copy build folder, MATLAB folder, data folder, demoX.m, LICENSE, README, testX.m into smlm_datafusion3d_matlab_minimal_win_1.0 and zip
- Run demoX.m again as a test
- Upload and be done

## Encrypted Matlab code, how to remove that part safely?

There are two p files. See also https://github.com/jkfindeisen/python_smlm_datafusion3d/issues/1

## Kernel Tuner by Ben van Werkhoven

Is used in the Python test code

Software at https://github.com/benvanwerkhoven/kernel_tuner
Publication at https://www.sciencedirect.com/science/article/pii/S0167739X18313359


