# Attention #

# !! #

# Transalyzer has moved to GitHub #
# https://github.com/voyn/transalyzer/ #

# !! #


![https://transalyzer.googlecode.com/svn/wiki/transalyzer.png](https://transalyzer.googlecode.com/svn/wiki/transalyzer.png)

---

This project consists of a series of Matlab based GUIs designed to:

  1. detect events in nanopore signals
  1. sort event populations / extract populations / remove clogs
  1. analyze events and generate various statistics
  1. detect and characterize spikes present within events

It was written by [Calin Plesa](http://www.calinplesa.com/) as part of his PhD research in the [Cees Dekker lab](http://ceesdekkerlab.tudelft.nl) at [Delft University of Technology](http://www.tudelft.nl).


---

# Reference #
If you use these scripts for your research, please cite:

C. Plesa & C. Dekker, _[Data analysis methods for solid-state nanopores](http://stacks.iop.org/0957-4484/26/084003)_. Nanotechnology 26 (2015) 084003.


---

# News #
_April 29, 2016_ - We have moved to GitHub. The new project URL is https://github.com/voyn/transalyzer/

_Mar 25, 2015_ - Unfortunately, Google Code will be shutting down this year. The project will be moving to a new repository soon.

_Feb 4, 2015_ - First public code release.


---

# Download #

Packaged releases:

_Mar 25, 2015_ - Download [Transalyzer RC1b](https://transalyzer.googlecode.com/svn/releases/transalyzer_rc1b.zip). Added ABF2.0 support and fixed issues with iterative detection. [Installation](https://code.google.com/p/transalyzer/wiki/Installation) guide. Further [documentation](https://code.google.com/p/transalyzer/wiki/Contents).

_Feb 4, 2015_ - Release of Transalyzer RC1a.


---

# Video Tutorials #

-[Intro video tutorial](https://www.youtube.com/watch?v=-21j8Pb6178)


---

# Documentation #

See the project [wiki](http://code.google.com/p/transalyzer/wiki/Contents) for all documentation, FAQs, guides, etc...


---

# Requirements #

  * Matlab R2011b (some features may not work on older versions)
    * Statistics Toolbox
    * Signal Processing Toolbox (some features)
    * [export\_fig](http://nl.mathworks.com/matlabcentral/fileexchange/23629-export-fig) (for publication quality figures)


---

# Features #
## Detection ##
![![](https://transalyzer.googlecode.com/svn/wiki/GUI_detect_small.png)](https://transalyzer.googlecode.com/svn/wiki/GUI_detect.png)
  * Supported Input File Formats
    * LabView TDMS (binary)
    * LabView DTLG (binary)
    * Axon ABF (binary) (currently only versions <2)
    * Axon Clampex ATF (text)
    * Text (two column (Time & Current), or single column (Current))
  * Splitting of files into small segments for detection
  * Save and auto load detection parameters
    * Analyze multiple experiments by auto-cycling through sub-folders
  * IV plot and data for Clampex IV files
  * Filtering options: None, Gaussian, Butterworth 2nd or 4th order
  * Input for Axon gain factor
  * Input for voltage (needed for conductance)
  * Plot options
    * Trace
      * Moving average
      * Sigma levels
      * Detection level
      * Detected events
    * Individual events
      * Current in nA or nS, with or without baseline removed
      * Browse through detected events
      * Individual event info
  * Detection Options
    * Baseline
      * Moving average
      * Manual input
      * Auto detect from current histogram peak
    * Sigma level
      * Full trace (low event rate, stable baseline)
      * Manual input
      * Auto detect from STD histogram peak
    * Iterative detection (as described in [Plesa and Dekker 2015](http://stacks.iop.org/0957-4484/26/084003))
    * Event type
      * Down (normal)
      * Up (low salt, [Smeets et al.](http://pubs.acs.org/doi/abs/10.1021/nl052107w))
      * Both ([Kowalczyk and Dekker](http://pubs.acs.org/doi/abs/10.1021/nl301719a))
    * Other input options
      * Peak detection factor (detection level = Sigma\*PDF)
      * Min and Max dwell time allowed
      * Extra points to save
      * Minimum gap between events (in points)
  * Dwell time: (1) FWHM (2) baseline crossing
  * Amplitude: (1) Maximum (for spikes) (2) Integral/FWHM (3) Between extreme local minima
  * Concatenate detected events
  * Tracking of experimental time for all data
  * Save options
    * Event traces and information
    * Unfiltered trace data
    * Export detected events to OpenNanopore

## Event Selection and Analysis ##
![![](https://transalyzer.googlecode.com/svn/wiki/GUI_events_small.png)](https://transalyzer.googlecode.com/svn/wiki/GUI_events.png)
### Selection Criteria ###
  * Dwell time
  * Amplitude
  * Baseline
  * Event number
  * Event Charge Deficit (Integral)

### Analysis ###
  * Event rate calculation
  * Event rate over experimental time ([Plesa et al.](http://pubs.acs.org/doi/abs/10.1021/nl3042678))
  * Gaussian / Multi-Gaussian fitting of dwell, amplitude, and current histogram distributions. ![![](https://transalyzer.googlecode.com/svn/wiki/GUI_gaussian_small.png)](https://transalyzer.googlecode.com/svn/wiki/GUI_gaussian.png)

### Output ###
  * Scatter, Scatter Histogram, Scatter Denisty (Amplitude vs Dwell time)
  * Dwell time histogram
  * Amplitude histogram
  * Current histogram
  * Integral histogram
  * Baseline vs event number
  * Pore resistance over time
  * Automated plot export

## Local Structures Detection and Analysis ##

![![](https://transalyzer.googlecode.com/svn/wiki/GUI_localstructures_small.png)](https://transalyzer.googlecode.com/svn/wiki/GUI_localstructures.png)

  * Detect and quantify spikes present within events.


---

# Source Code Acknowledgements #
Transalyzer uses various functions and code written by different people and provided for free. I would like to acknowledge their contributions in this section.
| **Name** | **Author** | **Licence** |
|:---------|:-----------|:------------|
| [abfload](http://www.mathworks.com/matlabcentral/fileexchange/6190) | Harald Hentschke | BSD         |
| [em\_1dim](http://homepages.cwi.nl/~pauwels/matlab_library/progs/clustering/cluster_1_dim/em_1dim.xml) | Eric Pauwels | Used with permission |
| [histnorm](http://www.mathworks.com/matlabcentral/fileexchange/22802-normalized-histogram) | Arturo Serrano | BSD         |
| [lmax, lmin](http://www.mathworks.com/matlabcentral/fileexchange/3170-local-min-max-nearest-neighbour) | Sergei Koptenko | BSD         |
| [movingstd](http://www.mathworks.nl/matlabcentral/fileexchange/9428-moving-window-standard-deviation) | John D'Errico | BSD         |
| [peakfinder](http://www.mathworks.nl/matlabcentral/fileexchange/25500-peakfinder) |  Nathanael Yoder | BSD         |
| [fwhm](http://www.mathworks.nl/matlabcentral/fileexchange/10590-fwhm) | Patrick Egan | BSD         |
| [TDMS Reader](http://www.mathworks.nl/matlabcentral/fileexchange/30023-tdms-reader) | Jim Hokanson | BSD         |

Additionally I would like to thank the following people for code contributions, bug reports, ideas, and productive discussions:
  * Auke Booij
  * Mathijs Rozemuller
  * [Nima Arjmandi](http://arjmandi.org) (See [Improved Algorithms for Nanopore Signal Processing](http://arxiv.org/abs/1207.2319))


---

# Future Feature List #
Here is a list of useful features which still remain to be implemented:
  * GUI\_detect: Split LabView binary files into segments
  * GUI\_detect: Determine filter delay, in order to sync filtered and unfiltered traces
  * GUI\_detect: A more elegant way to deal with the moving average at the start of the trace.
  * GUI\_detect: Open and analyze segments smaller than the segment file (at the end of abf files). Currently these are ignored, so several seconds of trace can be lost.
  * GUI\_detect: Finding the local baseline crossing point from the detection level crossing point is currently implemented with a while loop. This should be recoded with vector operations for improved speed.
  * GUI\_detect: Improved error catching code.
  * GUI\_detect: Optimize code to build the master event trace.
  * GUI\_events: Remove global variables (used for passing plot limits).
  * GUI\_events: Log dwell time histogram.
  * GUI\_events: Implement a moving average and threshold selection to the local baseline selection.
  * Command line versions of all of the scripts.


---

# It's Not A Bug It's A Feature #
Known bugs and issues:
  * GUI\_detect: The code treats short-duration spikes (only 1 local minimum) and longer events (>1 local minima) slightly differently. In certain situations this can lead to a discontinuity in the event populations around the transition area which is an analysis artifact.
  * GUI\_detect: When using abf files, it will only read segments equal to the segment time which is set. Since the total trace time in a abf file is typically not evenly divisible (without a remainder) by the segment time, a small part of the trace (several seconds) can be lost at the end of each file.


---

# Links #
  * [OpenNanopore](http://lben.epfl.ch/page-79460-en.html) - A Matlab based tool for data analysis of nanopore experiments that is based on the cumulative sums algorithm (CUSUM algorithm) developed by the [Radenovic Lab](http://lben.epfl.ch/) at [EPFL](http://epfl.ch).
  * [Pyth-ion](https://www.youtube.com/watch?v=5iEKgre1lbs) - pore analysis software from the [Wanunu Lab](http://www.northeastern.edu/wanunu/) at [Northeastern University](http://www.northeastern.edu/).
  * [Nanopore Analysis](http://people.bath.ac.uk/yl505/nanoporeanalysis.html) - Nanopore data analysis software developed by [Yi-Tao Long's group](http://people.bath.ac.uk/yl505/index.html) at [East China University of Science and Technology](http://www.ecust.edu.cn/).
  * [poretools](https://github.com/arq5x/poretools) - a toolkit for working with nanopore sequencing data from Oxford Nanopore.
  * [MOSAIC](http://usnistgov.github.io/mosaic/) - a modular single-molecule nanopore analysis toolbox to decode multi-state nanopore data.
  * [signalstepdetector](http://code.google.com/p/signalstepdetector/)  -  Matlab based algorithm for detecting multiple steps in nanopore signal