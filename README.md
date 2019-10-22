# DroneLight
Project for Intro to DS course @ Skoltech

### Overview:

STEPS
- collecting training and testing data 
- extracting features from IMU inputs 
- for each input gesture classifier needs to recognize the correct label
- draw visualization
- using this label as a key in dictionary we can send numpy array value to drone

###  IMU Data Reading

In  our  project,  the  user wears the glove and performs one of four gesture patterns. We  use  the  Arduino Nano, IMU sensor MPU-6050 and flex sensor,  shown  in  Figure 2 , as our data input source.  

When flex sensor bends more than some threshold - data recording starts, when flex sensor is relaxed - data recording stops. To prevent drift of IMU readings we perform automatic reset before each new recording.

IMU provides us with 6 degree of freedom sensor readings
    - gyroscopes
    - accelerometers 
Inputs  from  IMU  are  streaming  to  local  PC through Arduino which is connected by USB

In order for the dataset to be more variative, non-uniform and robust to noise gestures we recorded data:
    - clock-wise
    - counterclock-wise
    - at different pitch-roll angle
    - upside-down
    - using 5 different hands for larger range of motions
    - moving with different speed


### Training Data Collection

For each of the letters [S, k, o, l] we collect 100 [?] sets of data samples manually. Each data sample is a sequence of 
    - raw IMU sensor readings? (6 features)
    - Kalman-filtered? (3 features)
that has a pre-defined start and ending time. We also include a label describing the gesture pattern for each data sample. 

For the first iteration of the project, the proposed algorithm should map 4 input gestures to 4 letters, which correspond to 4 sets of flight setpoints.


### Data Pre-Processing and Feature Extraction

To classify a specific gesture pattern accurately, we need to take into account of both the pose and the position of glove.

- we normalize the gyroscope and accelerometer inputs
- we process all our input sequences to be the same length by sampling within the start-end window
- we create a synthetic data with transform operators and inversing order of the original recordings (for [x, y, z])
-  each of our input data sample is a sequence of ___ dimensional feature arrays representing the status of the glove at a specific time step



### The Drone part

these setpoints need to be sent to drone to follow this path

with numpy (x, y z) array make a drone to fly through these setponts (Roman)

control LED while flying

record the drone flight

Input: recorded gestures / path from glove with IMU

Output: drone light-painting the letter / word

### Improvements

- Recognize fake gestures?



