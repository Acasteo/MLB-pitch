# MLB-pitch
## By Isaac Golberg, Austin Castelo, and Ryan Bernstein

The goal of this analysis is to predict pitch type based on previous pitches thrown, score of the game, players on base, etc.

# To Do:

## (DONE) Data Preprocessing

### (DONE) Download atbats.csv, pull necessary variables, and merge with pitches.csv
(DONE) ab_id is the by/join variable to merge the csvs by
(DONE) Pull ab_id, batter_id, inning, p_score, p_throws, pitcher_id, stand, top

### (DONE) Remove the following variables:
(DONE) ax, ay, az, break_angle, break_length, break_y, code, pfx_x, pfx_z, px, pz, spin_dir, end_speed, sz_bot, sz_top, vx0, vy0, vz0, x, x_0, y, y_0, z, z_0, zone

### (DONE) pitch_type:
(DONE) Remove Unknown (UN) and Eephus (EP) 
(DONE) Combine FO and PO
(DONE) Remove AB and FA because each have 9 observations
(DONE) Remove SC because screwballs are not frequent

### (DONE) Dummy encode:
(DONE) pitch_type (consider combining similar types of pitches into single encoding)

### (DONE) Feature Engineering:
(DONE) Construct a single column (count_status) out of b_count, s_count (0=0-0, 1=1-0, 2=0-1, 3=1-1, 4=2-0, 5=0-2, 6=3-0, 7=2-1, 8=1-2, 9=3-1, 10=2-2, 11=3-2)
(DONE) Create variable (score_differnce) which is defined by b_score minus p_score
(DONE) Construct a single column (base_status) out of on_1b, on_2b, on_3b (0 = no one on base, 1 = 1st, 2 = 2nd, 3 = rd, 4 = 1st and second, ... , 7 = bases loaded)

### (DONE) Bin the following variables:
(DONE) score_difference: -5=(-25,-5), 5=(5,25), -4 through 4 don't get binned
(DONE) pitch_num: 0=(1,6) 1=(7,21)

### (DONE) Outlier Removal
(DONE) Remove all observations with Unknown (UN) and Eephus (EP) in the pitch_type column

# Now that preprocessing is complete, models should be constructed based on the preprocessed data. In order to work faster, we will create new .ipynb for different models so that people can work on separate tasks. Once completed, code will be uploaded to the master file. 

# The preprocessed data can be downloaded here: https://drive.google.com/file/d/1KHFvfbEOcqjxqP6r1Wr7QRsQBJRMdr9v/view?usp=sharing

## Data Splitting/Sampling
5-fold CV
No sampling
Split Data into train and test (80%/20% split)

## Exploratory Analysis (at least 2 graphs)
(DONE) Pie graph breakdown of pitch types (overall)
(DONE) Pie graph breakdown of pitch types (2 individual pitchers as a case study)
PCA graph

## Base Model
Regression Model (Needs to be basic as stated in directions):
use pitcher_id and count_status
