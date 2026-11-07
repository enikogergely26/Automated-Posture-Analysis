# Automated Posture Analysis

**Computer Vision-Based Baseball Hitting Posture Analysis**

**Author:** Enikő Gergely

## Project Overview

This project aims to automate the collection and analysis of baseball hitters' batting posture using computer vision techniques and video data from [Baseball Savant](https://baseballsavant.mlb.com/).

The project builds on my previous research on the relationship between Christian Yelich's batting posture and offensive performance. The original study involved manual image collection and posture measurements. This project develops an automated workflow to make the process more efficient, scalable, and applicable to multiple MLB players.

The primary focus is measuring the **Back-Gluteal angle** during a hitter's batting stance and investigating its potential relationship with offensive performance, particularly On-Base Percentage (OBP).

## Project Objectives

- Automate video and image collection from Baseball Savant.
- Develop an automated image-processing workflow to identify hitters and extract their body silhouettes.
- Calculate the Back-Gluteal angle from video frames.
- Validate the automated data collection process against previous manual analysis.
- Extend the analysis from a single player to a larger sample of MLB hitters.
- Investigate potential relationships between batting posture and offensive performance.

## Methodology

The automated workflow consists of the following main steps:

1. **Video Collection:** Download hitter videos from Baseball Savant for selected players and seasons.
2. **Frame Extraction:** Extract individual frames from the collected videos.
3. **Player Cropping:** Identify and crop the hitter from each frame.
4. **Image Processing:** Generate player silhouettes and identify the relevant body positions.
5. **Angle Calculation:** Draw the Back-Gluteal line and calculate its angle.
6. **Data Collection:** Store posture measurements together with game dates and player information.
7. **Performance Analysis:** Compare posture measurements with offensive statistics, primarily OBP.

Some image crops are manually reviewed to remove incorrectly identified images and improve the quality of the final measurements.

## Visual Workflow

The automated posture analysis pipeline consists of four main steps:

### 1. Original Video Frame
![Original frame](Notebooks%20-%20Posture%20Analysis/Yelich(592885)/hitting_frames_Yelich_2024/746006_c3d1ba39-0cc4-4056-8ace-796c8f0845fc-00000.png)

### 2. Player Detection & Cropping
![Cropped player](Notebooks%20-%20Posture%20Analysis/Yelich(592885)/cropped_images_Yelich_2024/cropped_image_746006_c3d1ba39-0cc4-4056-8ace-796c8f0845fc-00000.jpg)

### 3. Silhouette Detection (green) & Back-Gluteal line (red)
![Player silhouette and Back-Gluteal line](Notebooks%20-%20Posture%20Analysis/Yelich(592885)/angle_results_Yelich_2024/2024-04-06_cropped_image_746006_c3d1ba39-0cc4-4056-8ace-796c8f0845fc-00000.jpg)

### 4. Back-Gluteal Angle Calculation

<img width="798" height="49" alt="image" src="https://github.com/user-attachments/assets/b3e0ece3-5ebf-4888-8562-fea784d159b5" />


## Repository Structure

```text
Automated-Posture-Analysis/
│
├── Notebooks - Posture Analysis/
│   ├── 01_Collect Savant videos and frames.ipynb
│   ├── 02_Add Back_Gluteal line.ipynb
│   ├── 10_Christian Yelich Angle Data Analysis.ipynb
│   └── Yelich(592885)/
│
├── 2025 Analysis/
│   ├── 2025 Analysis - Data Collection.ipynb
│   ├── 2025 Analysis - Output Data Analysis.ipynb
│   ├── All_player_results.xlsx
│   ├── stats_with_team.csv
│   └── Sample results/Judge, Aaron(592450)/
│
└── README.md
```

## Analysis 1: Christian Yelich (2018–2026)

This analysis extends my previous research on Christian Yelich's batting posture and offensive performance.

The original study examined the relationship between his Back-Gluteal angle and batting statistics from 2018 to August 2023. This project automates the data collection and image-processing steps and extends the analysis through 2026.

**Notebooks:**

| Notebook | Description |
|---|---|
| `01_Collect Savant videos and frames.ipynb` | Downloads Baseball Savant videos, extracts frames, and crops the hitter from each image. |
| `02_Add Back_Gluteal line.ipynb` | Generates player silhouettes, draws the Back-Gluteal line, and calculates posture angles. |
| `10_Christian Yelich Angle Data Analysis.ipynb` | Analyzes posture measurements and compares them with batting performance over time. |

The analysis includes outlier removal, average angle comparisons, OBP comparisons, and moving averages to identify potential posture trends across seasons.

**Previous research:** [Christian Yelich Posture Analysis](https://github.com/enikogergely26/YelichPostureAnalysis/blob/main/Christian%20Yelich%20Posture%20Analysis%20-%20EnikoGergely.pdf)

## Analysis 2: MLB Hitters – 2025 Season

The second analysis expands the automated workflow to a larger sample of MLB hitters to investigate the relationship between batting posture and offensive performance across multiple players.

The initial sample includes **70 hitters from the 2025 season**.

### Data Collection

The `2025 Analysis - Data Collection.ipynb` notebook performs the following tasks:

- Downloads player information and batting statistics from Baseball Savant.
- Selects the first 70 hitters from the collected dataset.
- Downloads their 2025 batting videos.
- Extracts video frames and crops the hitters.
- Allows manual review of the cropped images to remove incorrect detections.
- Generates player silhouettes and calculates Back-Gluteal angles.
- Saves the collected measurements into an Excel output file.

### Output Files

| File | Description |
|---|---|
| `stats_with_team.csv` | Batting statistics and player information downloaded from Baseball Savant for the 2025 season. |
| `All_player_results.xlsx` | Consolidated output of the automated posture collection process for all analyzed players. |
| `Sample results/Judge, Aaron(592450)/` | Example output for an individual player (Aaron Judge). |

The consolidated Excel output includes:

- Image filename
- Game date
- Back-Gluteal angle
- Player name and ID
- Batting handedness
- Team ID

### Performance Analysis

The `2025 Analysis - Output Data Analysis.ipynb` notebook explores the relationship between the average Back-Gluteal angle and offensive performance (OBP) across the analyzed qualified hitters (more than 500 plate appearances).

The analysis includes:
- Outlier removal and calculation of average Back-Gluteal angles.
- Scatterplot visualizations comparing average angles with OBP across qualified hitters.
- A separate scatterplot including players from selected stadiums only, where silhouette detection is not affected by background objects or spectators.
- A separate scatterplot of selected hitters with high-quality angle measurements.

The results do not indicate a clear relationship between the average Back-Gluteal angle and OBP, either across the full sample or among the selected stadiums or hitters with more reliable measurements.

These results suggest that the Back-Gluteal angle alone may not be sufficient to explain differences in offensive performance across players. However, it may still provide useful insights at the individual player level, potentially helping identify posture changes that coincide with changes in batting performance. Combined with additional biomechanical variables, it could offer a more detailed understanding of individual performance trends and help identify potentially meaningful changes over time.

## Technologies & Tools

- Python
- Jupyter Notebook
- Computer Vision
- Video and Image Processing
- Baseball Savant data
- Data Analysis and Statistical Methods

## Limitations

Automated posture measurements can be affected by image quality, camera angles, and background objects. In some stadiums, spectators visible behind the hitter can interfere with silhouette detection and result in incorrect angle measurements.

Manual image review is therefore included as a quality-control step. Further improvements to silhouette detection and image processing could help reduce these errors and make the workflow more fully automated.

## Future Work
- Explore whether changes in posture can help identify meaningful changes in offensive performance.
- Implement pose estimation using MMPose framework, including RTMPose models to extract detailed skeletal keypoints and joint coordinates from hitter images. Analyze the resulting joint-level data to identify additional biomechanical patterns and potentially useful features related to batting performance.
- Improve silhouette detection and angle calculation accuracy.
- Expand the analysis to additional MLB hitters and seasons.
