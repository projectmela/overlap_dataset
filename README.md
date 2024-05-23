This repository contains two jupyter notebooks.
- id_matching.ipynb
- mapping_statistics.ipynb

Below, I describe the requirements fo each of the notebooks and what they do.

# 1. id_mapping.ipynb

## Overview
This Jupyter Notebook performs ID mapping between two videos, utilizing manual corrections and plotting videos with color-coded tracklets. It reads tracking data from CSV files, processes the data to map IDs between two videos, and generates visual outputs to verify the mappings.

## Requirements
- Python 3.x
- Required libraries: `numpy`, `pandas`, `matplotlib`, `cv2` (OpenCV), `sys`

## Output
The output of this jupyter notebook is a CSV file that contains mapping of individual IDs between the two videos while accounting for lag (the fact that the two videos are not synchronised in time). The output CSV contains the following columns:

start_frame_<file1>: Starting frame number for the object in the first video.
end_frame_<file1>: Ending frame number for the object in the first video.
lagged_start_frame_<file1>: Starting frame number for the object in the first video while accounting for lag.
lagged_end_frame_<file1>: Ending frame number for the object in the first video while accounting for lag.
ID_<file1>: Unique identifier for objects in the first video.
start_frame_<file2>: Starting frame number for the object in the second video.
end_frame_<file2>: Ending frame number for the object in the second video.
lagged_start_frame_<file2>: Starting frame number for the object in the second video while accounting for lag.
lagged_end_frame_<file2>: Ending frame number for the object in the second video while accounting for lag.
ID_<file2>: Unique identifier for objects in the second video.
overlap_duration: The duration in frames when the two tracklets overlap.

Note that the lag is always expressed as the frame number in file2 - frame number in file1 in a moment when both videos are synchronised. Additionally, the overlap is calculated on the lagged frames.

# 2. mapping_statistics.ipynb

## Overview
This Jupyter Notebook calculates and compiles statistics from ID mapping between multiple pairs of videos. It reads mapping data from CSV files, computes various statistics for the mappings, and saves the results to a new CSV file.

## Requirements
- Python 3.x
- Required libraries: `numpy`, `pandas`, `matplotlib`

## Output
There are two output CSV files that result from this script. The first file contains the mapping results between the two videos and serves as a summary of the ID mappings and provides key statistics for further analysis. It includes the following columns:

set_id: Identifier for the set of videos being processed.
video_1: Filename of the first video in the mapping.
video_2: Filename of the second video in the mapping.
id_matches: Number of ID matches found between the two videos.
shortest_tracklet: Duration of the shortest tracklet in the mapping.
average_tracklet: Average duration of the tracklets in the mapping.
longest_tracklet: Duration of the longest tracklet in the mapping.

The second file contains all tracklets in the dataset and includes the following columns:

set_id: Identifier for the set of videos being processed.
video_1: Filename of the first video in the mapping.
video_2: Filename of the second video in the mapping.
tracklet_duration: Duration of the mapped tracklet in consideration.
