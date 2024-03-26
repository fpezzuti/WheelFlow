# WheelFlow Data Analysis

This [directory](./) contans all the Python code and the Jupyter notebooks used for analyzing the data collected by the [RecordApplication](./../RecordApplication).

## Data analysis
In the [`data_analysis.py`](./data_analysis.py) can be found the final pipeline used for the data analysis and segmentation tasks.

The pipeline consists in:  
1. **import the segmented datasets** from the `.csv` files contained in the [data folder](./data)   
2. for each dataset, **rename the features** and **convert class labels into numerical attributes** according to the classification type (binary or multiclass)
3. perform **normalization**, **feature selection** with different importance indexes, and **rebalancing**
4. for each set of dataset, classification type and importance index, perform a **10-fold cross-validation** using various classifiers
6. **save the results** in the [`classification_results.csv`](./classification_results.csv) file.

All the code is containedin the Jupyter notebooks in the [python](./python) folder.

## Data visualization & PCA

- to **visualize and plot the data**, the [data visualization notebook](./python/datavisualization.ipynb) can be used.
- to plot data in two dimensions, the [PCA notebook](./python/PCA.ipynb) can be used.

## Data cleaning
In the [data cleaning notebook](./python/datacleaning.ipynb) notebook the raw data received from the smartphone sensors is cleaned and prepared for the data segmentation and the feature extraction.  

The `.csv` data were imported, and the script removes the rows in which 2/3 of the features are 0 (non-meaningful record); then the three columns from each smartphone sensor are aggregated with the norm of the three coordinates (i. e. `ACC_X`, `ACC_Y`, `ACC_Z` -> `ACC` = `|ACC_X^2 + ACC_Y^2 + ACC_Z^2|`)

## Segmentation

The [segmentation notebook](./python/segmentation.ipynb) contains the code for **segmenting the cleaned data** and **extracting the features from each window**.  

The script follows these **steps**: 
1. **creates the *macro windows***, one for each recording.
2. from each macro window, **creates the actual *windows***.
3. applies the **wavelet transformation** to time domain's features (one for each sensor), obtaining 2 additional features for each sensor.
4. **extracts the aggregated features** from each window
5. **exports the dataset** in a `.csv` file

The segmentation notebook has three **parameters**:
- `OFFSET`: distance between two different macro windows, in seconds
- `WINDOW`: width of a single time window, expressed in seconds
- `OVERLAP`: size of the overlapping region between two adjacent windows

The **features extracted** from each window are _min_, _max_, difference between _min_ and _max_, _kurtosis_, _skewness_, _mean_, _standard deviation_, _median_, _energy_, 1st and 3rd _quartiles_, and the _number of peaks for each cleaned feature_, with a total of **117 features**.
