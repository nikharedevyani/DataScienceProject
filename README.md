# DataScienceProject
MSc Data Science final semester dissertation project

Information about dataset used for this project

#Dataset Information
The PAMAP2 Physical Activity Monitoring dataset contains data of 18 different physical activities (such as walking, cycling, playing soccer, etc.), performed by 9 subjects wearing 3 inertial measurement units and a heart rate monitor. The dataset can be used for activity recognition and intensity estimation, while developing and applying algorithms of data processing, segmentation, feature extraction and classification.

** Sensors **
3 Colibri wireless inertial measurement units (IMU):
  - sampling frequency: 100Hz
  - position of the sensors:
       - 1 IMU over the wrist on the dominant arm 
       - 1 IMU on the chest 
       - 1 IMU on the dominant side's ankle 
HR-monitor:
  - sampling frequency: ~9Hz

** Data collection protocol **
Each of the subjects had to follow a protocol, containing 12 different activities. The folder â€œProtocolâ€ contains these recordings by subject.
Furthermore, some of the subjects also performed a few optional activities. The folder â€œOptionalâ€ contains these recordings by subject.

** Data files **
Raw sensory data can be found in space-separated text-files (.dat), 1 data file per subject per session (protocol or optional). Missing values are indicated with NaN. One line in the data files correspond to one timestamped and labeled instance of sensory data. The data files contain 54 columns: each line consists of a timestamp, an activity label (the ground truth) and 52 attributes of raw sensory data.

#Additional Variable Information
The 54 columns in the data files are organized as follows:
  1.		timestamp (s)
  2.		activityID (see below for the mapping to the activities)
  3.		heart rate (bpm)
  4-20.		IMU hand
  21-37.	IMU chest
  38-54.	IMU ankle

The IMU sensory data contains the following columns: 
  1.		temperature (Â°C) 
  2-4.		3D-acceleration data (ms-2), scale: Â±16g, resolution: 13-bit 
  5-7.		3D-acceleration data (ms-2), scale: Â±6g, resolution: 13-bit
  8-10.		3D-gyroscope data (rad/s) 
  11-13.	3D-magnetometer data (Î¼T) 
  14-17.	orientation (invalid in this data collection) 

List of activityIDs and corresponding activities:
 1	lying
 2	sitting
 3	standing
 4	walking
 5	running
 6	cycling
 7	Nordic walking
 9	watching TV
 10	computer work
 11	car driving
 12	ascending stairs
 13	descending stairs
 16	vacuum cleaning
 17	ironing
 18	folding laundry
 19	house cleaning
 20	playing soccer
 24	rope jumping
 0	other (transient activities)
