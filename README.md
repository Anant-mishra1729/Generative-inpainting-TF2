# Generative Image Inpainting (Tensorflow 2 support)
## Original version by Jiahui Yu is here: [Generative Image inpainting](https://github.com/JiahuiYu/generative_inpainting)
An open source framework for generative image inpainting task, with the support of [Contextual Attention](https://arxiv.org/abs/1801.07892) (CVPR 2018) and [Gated Convolution](https://arxiv.org/abs/1806.03589) (ICCV 2019 Oral).


> **Warning** :
> I have used this updated code only for testing (or reproducing results).

### Tested on
* Ubuntu 22.04


### Instructions 
> Prefer using conda for python environment creation.
* Tensorflow (Install using [Pip](https://www.tensorflow.org/install/pip)).
* Install openCV `pip install opencv-contrib-python`.
* Install tf_slim `pip install tf-slim`.
* Install yaml `pip install PyYAML`.
* Instal neuralgym `pip install git+https://github.com/JiahuiYu/neuralgym`.
  
  Go to the directory **`site-packages`** where all python packages of current python environment are stored and run this command:
    ```sh
    tf_upgrade_v2 --intree neuralgym/ --outtree neuralgym/ --reportfile report.txt
    ```
   

## For testing
### Pretrained models

[Places2](https://drive.google.com/drive/folders/1y7Irxm3HSHGvp546hZdAZwuNmhLUVcjO?usp=sharing) | [CelebA-HQ](https://drive.google.com/drive/folders/1uvcDgMer-4hgWlm6_G9xjvEQGP8neW15?usp=sharing)

Download the model dirs and put it under `model_logs/` (rename `checkpoint.txt` to `checkpoint` because google drive automatically add ext after download). Run testing or resume training as described above. All models are trained with images of resolution 256x256 and largest hole size 128x128, above which the results may be deteriorated. We provide several example test cases. Please run:

```bash
# Places2 512x680 input
python test.py --image examples/places2/case1_input.png --mask examples/places2/case1_mask.png --output examples/places2/case1_output.png --checkpoint_dir model_logs/release_places2_256
# CelebA-HQ 256x256 input
# Please visit CelebA-HQ demo at: jhyu.me/deepfill
```

**Note:** Please make sure the mask file completely cover the masks in input file. You may check it with saving a new image to visualize `cv2.imwrite('new.png', img - mask)`.


## Citing
```
@article{yu2018generative,
  title={Generative Image Inpainting with Contextual Attention},
  author={Yu, Jiahui and Lin, Zhe and Yang, Jimei and Shen, Xiaohui and Lu, Xin and Huang, Thomas S},
  journal={arXiv preprint arXiv:1801.07892},
  year={2018}
}

@article{yu2018free,
  title={Free-Form Image Inpainting with Gated Convolution},
  author={Yu, Jiahui and Lin, Zhe and Yang, Jimei and Shen, Xiaohui and Lu, Xin and Huang, Thomas S},
  journal={arXiv preprint arXiv:1806.03589},
  year={2018}
}
```
