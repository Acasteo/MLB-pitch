# MLB-pitch
## By Isaac Golberg, Austin Castelo, and Ryan Bernstein

The goal of this analysis is to predict pitch type based on previous pitches thrown, score of the game, players on base, etc.

# To Do:

                                              ## Data Preprocessing
### Download atbats.csv, pull necessary variables, and merge with pitches.csv
ab_id is the by/join variable to merge the csvs by
Pull ab_id, batter_id, inning, p_score, p_throws, pitcher_id, stand, top

### Remove the following variables:
ax, ay, az, break_angle, break_length, break_y, code, pfx_x, pfx_z, px, pz, spin_dir, end_speed, sz_bot, sz_top, vx0, vy0, vz0, x, x_0, y, y_0, z, z_0, zone

### pitch_type:
Remove Unknown (UN) and Eephus (EP) 
Combine FO and PO

### Dummy encode:
pitch_type (consider combining similar types of pitches into single encoding)

### Feature Engineering:
Construct a single column (count_status) out of b_count, s_count (0=0-0, 1=1-0, 2=0-1, 3=1-1, 4=2-0, 5=0-2, 6=3-0, 7=2-1, 8=1-2, 9=3-1, 10=2-2, 11=3-2)
Create variable (score_differnce) which is defined by b_score minus p_score
Construct a single column (base_status) out of on_1b, on_2b, on_3b (0 = no one on base, 1 = 1st, 2 = 2nd, 3 = rd, 4 = 1st and second, ... , 7 = bases loaded)

### Bin the following variables:
score_difference: -5=(-25,-5), 5=(5,25), -4 through 4 don't get binned
pitch_num: 0=(1,6) 1=(7,21)
pitch_type: PO=(FO, PO) So just rename FO as PO

### Outlier Removal
Remove all observations with Unknown (UN) and Eephus (EP) in the pitch_type column

                                            ## Data Splitting/Sampling
5-fold CV
No sampling
Split Data into train and test (80%/20% split)

                                     ## Exploratory Analysis (at least 2 graphs)
Pie graph breakdown of pitch types (overall)
Pie graph breakdown of pitch types (2 individual pitchers as a case study)
PCA graph


                                             ## Base Model
Regression Model (Needs to be basic as stated in directions):
use pitcher_id and count_status
