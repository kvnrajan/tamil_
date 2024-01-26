# Tamil OCR 

Finetuned version of PARSEQ model on Tamil text. This version of OCR is much more robust to tilted text compared to the Tesseract, Paddle OCR and Easy OCR. Works best for text present in everday's life (scene texts). This model is work in progress, feel free to contribute!!!

Currently supports two languages (English + Tamil). Accuracy of the model can be improved by adjusting the Text detection model as per your requirements. Achieved the accuracy of around **>95%** (98% NED) in validation set

## OUTPUT

 Input Image                                                                | TAMIL OCR             | Tesseract         | 
|:--------------------------------------------------------------------------:|:--------------------:|:-----------------:|
| <img width="200" alt="teaser" src="./test_images/4.jpg">                   | வாழ்கவளமுடன்     |    க்‌ க்கஸாரகளள௮ஊகஎளமுடன்‌    | 
| <img width="200" alt="teaser" src="./test_images/10.jpg">                  | ரெடிமேட்ஸ்          |**NO OUTPUT**      | 
| <img width="200" alt="teaser" src="./test_images/2.jpg">                   | கோபி               | **NO OUTPUT**            | 
| <img width="200" alt="teaser" src="./test_images/6.jpg">                   | தாம்பரம்            | **NO OUTPUT** | 
| <img width="200" alt="teaser" src="./test_images/1.jpg">                   | நெடுஞ்சாலைத்      | **NO OUTPUT**             | 

**Tesseract results are tested using the [huggingface space](https://huggingface.co/spaces/kneelesh48/Tesseract-OCR) with Tamil as language**

## How to use
1. Clone the repository
2. Pip install the required modules using
3. Download the models weights from the [GDRIVE](https://drive.google.com/drive/folders/1oMxdp7VE4Z0uHQkHr1VIrXYfyjZ_WwFV?usp=sharing) and keep it under model_weights 
    
        |___model_weights
            |_____craft_mlt_25k.pth
            |_____parseq_tamil.ckpt
    
4. Run the below code by providing the path 

**Text Recognition**

```python
from tamil_ocr import OCR

image_path = r"test_images\1.jpg" # insert your own path here
ocr = OCR()
texts = ocr.predict(image_path)
with open("output.txt","w",encoding="utf-8") as f:
    f.write(texts)

>>>> நெடுஞ்சாலைத்

```

**Text Detect + Recognition**

```python
from tamil_ocr import OCR

image_path = r"test_images\0.jpg" # insert your own path here
ocr = OCR(detect=True)
texts = ocr.predict(image_path)
with open("output.txt","w",encoding="utf-8") as f:
    f.write(texts)

>>>> கொடைக்கானல் Kodaikanal 

```

## LIMITATIONS

Unable to read the text if they are present in rotated forms

<img width="200" alt="teaser" src="./test_images/8.jpg"> 
<img width="200" alt="teaser" src="./test_images/9.jpg">


## Thanks to the below contibuters for making awesome Text detection and text recognition models

**Text detection** - [CRAFT TEXT DECTECTION](https://github.com/clovaai/CRAFT-pytorch)

**Text recognition** - [PARSEQ](https://github.com/baudm/parseq)


```bibtex
@InProceedings{bautista2022parseq,
  title={Scene Text Recognition with Permuted Autoregressive Sequence Models},
  author={Bautista, Darwin and Atienza, Rowel},
  booktitle={European Conference on Computer Vision},
  pages={178--196},
  month={10},
  year={2022},
  publisher={Springer Nature Switzerland},
  address={Cham},
  doi={10.1007/978-3-031-19815-1_11},
  url={https://doi.org/10.1007/978-3-031-19815-1_11}
}
```

```bibtex
@inproceedings{baek2019character,
  title={Character Region Awareness for Text Detection},
  author={Baek, Youngmin and Lee, Bado and Han, Dongyoon and Yun, Sangdoo and Lee, Hwalsuk},
  booktitle={Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition},
  pages={9365--9374},
  year={2019}
}
```

## CITATION

```bibtex
@InProceedings{Gnana Prasath,
  title={Tamil OCR},
  author={Gnana Prasath D},
  month={01},
  year={2024},
  url={https://github.com/gnana70/tamil_ocr}
}
```