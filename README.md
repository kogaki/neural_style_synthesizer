neural_style_synthesizer
==========================

INSTALL
---------------

```
pip install -r requirements.txt
```

RUN
----------------

### Whole style transfer

You can transfer whole patch from one to another.

with CPU

```
python bin/convert_image_multi.py \
  --iteration=100 \
  --gpu=-1 \
  --xsplit=1 --ysplit=1 --resize=300 \
  input.png \
  style.png \
  --output_image=./converted.png
```

with GPU

```
python bin/convert_image_multi.py \
  --iteration=100 \
  --gpu=0 \
  --xsplit=1 --ysplit=1 --resize=300 \
  input.png \
  style.png \
  --output_image=./converted.png
```

### Partial style transfer

Choose optimal patches from style image and transfer them to another image.
Split style image to 2x2

```
python bin/convert_image_multi.py \
  --iteration=100 \
  --gpu=0 \
  --xsplit=2 --ysplit=2 --resize=300 \
  --model=vgg_nopad\
  input.png \
  style.png \
  --output_image=./converted_optimal_2x2.png
```

### Style transferred video

Tranfer style on video frame using last frame's result.

```
python bin/convert_video.py \
  --iteration=100 --model=vgg \
  video.mp4 \
  style.png \
  output_directory
```

Then you can find the style transferred video at `output_directory/out.avi` after 100 x frame times calculation.
