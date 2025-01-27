Dataset (zip folder):

1. data (data4) - This dataset was collected using donkeycar's built-in manage.py. Collect by Yuyang and Zhongzheng. 13103 clean images with purely joystick operating. Drive wild in the track but keep the donkeycar would not hit the wall. We don't deliberately follow the orange guide line when driving. The speed (throttle) is not constant, sometimes fast and sometimes slow. Also tried to drive along the outer wall and the inner wall to collect more edge images. 
The model trained using this dataset did not perform well.
Image flip-method: 2, change the flip-method number in 0206.py to test model that trained by this dataset

2. dirty_images_12.22 - Obtained by Yuang, contains 5 kinds of dirty image: green marker, hit wall, white plastic, yellow plastic, rain drop. These images are used as a dirty dataset to be added to the clean dataset and investigate their impact on the trained model.
Image flip-method: 6, only add to the dataset that has flip-method = 6

3. my_data (data) - This dataset was collected using collect_data.py which designed by undergrad student. Collect by Yuang and Yuyang. 10305 clean images with joystick control the steer value and keyboard control throttle. The car tends to follow the guide line in the middle of the track, but not completely. The speed is very slow, controlled by the keyboard to maintain a minimum driving speed.
Image flip-method: 6, change the flip-method number in 0206.py to test model that trained by this dataset

4. my_data2 (data2) - This dataset was collected using collect_data.py which designed by undergrad student. Collect by Yuyang and Zhongzheng. 13579 clean images with joystick control the steer value and keyboard control throttle. Follow the orange guide lines exactly when driving.
Image flip-method: 6, change the flip-method number in 0206.py to test model that trained by this dataset

5. my_data3 (data3) - This dataset was collected using collect_data.py which designed by undergrad student. Collect by Yuyang and Zhongzheng. 14055 clean images with purely joystick operating. Drive wild in the track but keep the donkeycar would not hit the wall. We don't deliberately follow the orange guide line when driving. The speed (throttle) is not constant, sometimes fast and sometimes slow. Also tried to drive along the outer wall and the inner wall to collect more edge images. 
Image flip-method: 2, change the flip-method number in 0206.py to test model that trained by this dataset

CNN Models (.h5):

Model naming conventions: models created by Yuyang usually name as: model_bt_n_b#_e#_data#.h5
bt: better, without bt means use Sam's model architecture
n: normalized input images
b/bs: batch size
e/ep: epochs
data: trained dataset
Some other name meaning:
fdirty: added dirty images that has fixed value for steer (1)
rdirty: added dirty images that has random assigned value for steer (random between -1 to 1)

0206.h5 - Sam's best model that performs very good in the track. Use a relatively simple 3-layer convolutional layer with tanh activation. There is currently no way to reproduce this model. Use epoch=3000 during training to overfit the model to the outer wall. The model reacts very well to the wall on the track and will not hit the wall even if you drive a little faster. The training set used may be 'data_0202', which uses a different track than the current track. The model outputs very strange steer values ​​in most tests, and the performance index is also very low, but it does not affect its excellent performance on the track. The track performance of this model is currently used as the comparison for the baseline model.

model_bt_n_b32_e200_data.h5 - Yuyang's best model performs a little worse than Sam's model at high speeds, but can complete the track normally at slow speeds. The model architecture is more complex, but can be reproduced with the same code (same training set, architecture and hyperparameters). The training set used 'my_data'. The track performance is also obvious to the outer wall. However, the recovery ability after turning at higher speeds is poor. We are currently looking for better hyperparameters or datasets based on this model to help build a baseline model trained with a clean dataset.

Edited by Yuyang at 01/27/2025