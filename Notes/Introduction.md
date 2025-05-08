## Objective

Simulate the natural radioactive decay of a bulk amount of a single isotope and track the change in isotopes over time, making use of experimental nuclear data.

## Data source

- The data is being sourced from the International Atomic Energy Agency (IAEA) using the NUBASE2020 data set ([Data](https://www-nds.iaea.org/amdc/ame2020/nubase_4.mas20.txt)).

### Key data

For now the key data to use form the NUMBASE2020 data set will be:
- The proton (Z) and mass (A) number for isotopes
- Half life of isotopes
- Decay modes (including the branching ratios)
- Daughter isotopes of decays

## Intended workflow

### 1. [[Data Preparation|Prepare the data]]

The NUMBASE2020 dataset is an ASCII file with fix-width data fields, the first process will be parsing this data to a new file, removing superfluous data and ensuring ease of use down the line.

This will be done by extracting the required information for each isotope (Z, A, half-life, decay modes etc), cleaning the data to a standardised way (e.g. all half-lifes in same units) and writing to a new CSV file.

### 2. Create Isotope class

A custom Isotope class will be defined containing:

- Key data for instance of isotope class (A, Z, half-life etc)
- Methods to:
	- determine random decay using RNG
	- perform different decay methods

### 3. Simulation loop

N nuclei will be initialised in a 1D data structure (this is TBD - possible a vector in C++ to allow resizing with increasing number of nuclei, this will allow the implementation of spontaneous fission (SF)) - with the array iterated over for each time step.

In each time step, for each nuclei, the code will:
- Check for a decay using RNG
- If decay is decided choose ta decay mode based on given ratios
- Spawn daughter isotope(s) (multiple if/when including SF)

**Note** - To begin with, the simulation will only be concerned with basic nuclear decays (alpha/beta), however the code will be written with the intention of being able to add rare decay modes such as SF.

### Results 

The aim will be to visualise the results in as many ways as possible, but as a minimum a graphical representation of changes in isotope counts over time.

The results can also be compared to the theoretical results based on the standard equation for nuclear decay:
## $A = A_0 e^{-\lambda t}$