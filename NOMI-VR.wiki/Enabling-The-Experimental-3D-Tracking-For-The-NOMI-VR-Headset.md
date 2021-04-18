#### Setting up the Experimental 3D Tracking For The NOMI VR Headset

The tracking is still very experimental and can only be run on NVIDIA GPU due to the usage of CUDA. The tracking makes uses of only a video input and an Artificial Neural Network AI trained to estimate a 3D body position. 

This method is nothing close to the precision or freedom of movements of a dedicated sensor however we believe that the model can be trained and improved by orders of magnitude.

You first need to connect a webcam to your computer and install Python 3.8.4 and select the option to add it to the path. Then install `PyTorch`, you can do so by running the following commands:

`python -m pip install torch===1.6.0 torchvision===0.7.0 -f https://download.pytorch.org/whl/torch_stable.html`

Then proceed to install `CUDA Toolkit 11.0.`

You’ll then need to download the Folder `PYTHONPATH` at https://github.com/https://github.com/NOMI-VR/NOMI-VR/Releases and add its location to `PyPath` in the `NOMI-VR/NOMI-VR_Headset/Build/nomivr_Driver/nomivr/resources/settings/default.vrsettings`

Set `tracking` to 1. The tracking is now turned on and can be turned off anytime by setting `tracking` to 0. The tracking can also be calibrated depending on your camera, this can be done by tweaking `scalesCoordinateMeter` and `offsetCoordinate`. `scalesCoordinateMeter` correspond to the delta of coordinates in a given axis calculated by the AI after normalization when you move 1 meter in that given axis.

**Note:** If you plan on using mpu9250 firmware do not forget to switch to it in the driver by setting `hmdIMUdmpPackets` to `false`:
`"hmdIMUdmpPackets":  false,`
