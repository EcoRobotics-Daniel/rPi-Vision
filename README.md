# Description

This is Eco Robotic's vision system. It will run on a raspberry pi as a coprocessor. The rPi will have this os: https://github.com/wpilibsuite/FRCVision-pi-gen/releases.

The vision processing pipeline was created using GRIP, an open-source software developed for FRC vision processing.

# Modifing Pipeline

## Modifing Manually

In order to modify the pipeline manually, go to the GripPipeline file, and change the values. The pipeline is built based on
OpenCV, so use that to modify.

## Modifing with Grip

The recommended way to modify the vision processing pipeline is to use GRIP. Once you are happy with the results in grip, generate the Java code.
Replace the GripPipeline file with the new one you just created, and make sure to change the line in the pipeline that says: public class GripPipeline
to say public class GripPipeline implements VisionPipeline. Build the code, and you should be good to go.

# Building on desktop

## Building


Java 11 is required to build.  Set your path and/or JAVA_HOME environment
variable appropriately.

1) Run "./gradlew build"

## Deploying

On the rPi web dashboard:

1) Make the rPi writable by selecting the "Writable" tab
2) In the rPi web dashboard Application tab, select the "Uploaded Java jar"
   option for Application
3) Click "Browse..." and select the "java-multiCameraServer-all.jar" file in
   your desktop project directory in the build/libs subdirectory
4) Click Save

The application will be automatically started.  Console output can be seen by
enabling console output in the Vision Status tab.

# Building locally on rPi

1) Run "./gradlew build"
2) Run "./install.sh" (replaces /home/pi/runCamera)
3) Run "./runInteractive" in /home/pi or "sudo svc -t /service/camera" to
   restart service.
