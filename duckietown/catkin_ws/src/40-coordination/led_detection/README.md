# Package `led_detection` {#led_detection}

<move-here src='#led_detection-autogenerated'/>

## LED detection

Pick your favourite duckiebot as the observer-bot. Refer to it as `![robot name]` for this step. If you are in good company, this can be tried on all the available duckiebots. First, activate the camera on the observer-bot:

    $ roslaunch duckietown camera.launch veh:=![robot name]

In a separate terminal, fire up the LED detector and the custom GUI by running:

    $ roslaunch led_detection LED_detection_with_gui.launch veh:=![robot name]

NOTE: to operate without a GUI:

    laptop $ roslaunch led_detection led_detection.launch veh:=![robot name]

The LED_detection_node will be launched on the robot, while LED_visualizer (a simple GUI) will be started on your laptop. Make sure the camera image from the observer-bot is visualized and updated in the visualizer (tip: check that your camera cap is off).

Hit on Detect and wait to trigger a detection. This will not have any effect if LED_detection_node is not running on the duckiebot (it is included in the above launch file). After the capture and processing phases, the outcome will look like:

The red numbers represent the frequencies directly inferred from the camera stream, while the selected detections with the associated signaling frequencies will be displayed in green.
You can click on the squares to visualize the brightness signals and the Fourier amplitude spectra of the corresponding cells in the video stream. You can also click on the camera image to visualize the variance map.


## Unit tests


To run the unit tests for the LED detector, you need to have the F23 rosbags on you hard disk. These bag files should be synced from [this dropbox link] (https://www.dropbox.com/sh/5kx8qwgttu69fhr/AAASLpOVjV5r1xpzeW7xWZh_a?dl=0).

For the test to locate the bag files, you should have the  `DUCKIETOWN_DATA` environment variable set, pointing to the location of you duckietown-data folder. This can be achieved by:

    $ export DUCKIETOWN_DATA=![local-path-to-duckietown-data-folder]

All the available tests are specified in file `all_tests.yaml` in the  scripts/ folder of the package led_detection in the duckietown ROS workspace. To run these, use the command:

    $ rosrun led_detection unittests.py ![algorithm] ![name-of-test]

Currently, `![algorithm]` can be either ‘baseline’ or ‘LEDDetector_plots’ to also display the plot in the process.

To run all test with all algorithms, execute:

    $ rosrun led_detection unittests.py '*' '*'


More in general:

    $ rosrun led_detection unittests.py ![tests] ![algorithms]

where:

- `![tests]` is a comma separated list of algorithms. May use "`*`".
- `![algorithms]` is a  comma separated list of algorithms. May use  "`*`".

The default algorithm is called "`baseline`", and its tests are invoked using:

    $ rosrun led_detection <script> '*' 'baseline'