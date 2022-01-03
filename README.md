# Channel Aware Reactive Mechanism (ChARM)

This repo hosts the source code we have used for the ChARM project [1] at the Institute for the Wireless Internet of Things at Northeastern University.
ChARM is a framework for a O-RAN reacting 3GPP base station. Please see [1] for system design and a comprehensive list of features.
ChARM leverages machine learning (specifically, a _residual neural network_) to sense and classify the spectrum usage, and employs customizable policies for dynamically reconfigure the 3GPP compliant network.
The goal of ChARM is to __intelligently optimize the wireless spectrum usage__, avoiding interference and exploiting the available unused bandwidth in mobile O-RAN/3GPP networks.

This repo has the following submodules:
 - srsRAN: a modified version of [srsRAN](https://github.com/srsran/srsRAN), extended with an API for dynamic cell reconfiguration (branch _charm_api_). It also sports a _colosseum_ feature branch which allows the execution of srsRAN on the [Colosseum](https://www.northeastern.edu/colosseum/) wireless emulator. If you want to use it on Colosseum, simply merge the branch _colosseum_ with the branch _charm_api_.
 - srsRAN_config: a collection of configuration files for srsRAN. Use the _charm_ folder for creating a base station with two cells; this configuration is specifically tweaked for Colosseum.
 - charm_mander: this is the AI-enabled driver for the base station, implementing the intelligence. Refer to its README for further information.
 - charm_mander/charm_trainer: this is the framework for training the machine learning model anew.

## Initialize repos

```
git submodule init
git submodule update
cd charm_mander
git submodule init
git submodule update
cd ..
```

## ChARM work

ChARM stems from a research project at the Northeastern University [1], if you use this code, please cite our work:

```
@inproceedings{Baldesi2022Charm,
  author = {Baldesi, Luca and Restuccia, Francesco and Melodia, Tommaso},
  booktitle = {{IEEE INFOCOM 2022 - IEEE Conference on Computer Communications}},
  title = {{ChARM: NextG Spectrum Sharing Through Data-Driven Real-Time O-RAN Dynamic Control}},
  year = {2022},
  month = may 
}
```

## ChARM dataset

ChARM machine learning model has been trained with a dataset for training, validation, and testing, which is publicly available [2].
The dataset was collected using Xilinx and USRP SDRs running the [OpenWiFi](https://github.com/open-sdr/openwifi) and [srsRAN](https://github.com/srsran/srsRAN) software stacks.

## References

1. L. Baldesi, F. Restuccia and T. Melodia. "ChARM: NextG Spectrum Sharing Through Data-Driven Real-Time O-RAN Dynamic Control", IEEE INFOCOM 2022 - IEEE Conference on Computer Communications, May 2022.
2. http://hdl.handle.net/2047/D20423481
