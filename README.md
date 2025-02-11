# **ShadeFusion BW: Dual-Tone Foundation Matching Algorithm**


## **Project Overview**
The **ShadeFusion BW** project addresses the **lack of diverse skin tone representation in foundation brands**. Despite attempts by major beauty retailers like Sephora to make foundations more accessible, there is still a **brand-specific gap in shade inclusivity**, particularly for darker skin tones. This project aims to create an algorithm that enhances foundation matching accuracy across brands by leveraging **computer vision and color theory**.

## **Research Question**
Can we develop a **computer vision-based skin-tone detection and foundation matching methodology** that provides a more accurate match across various brands?

## **Background**
- Skin tones exist on a **gradient**, not just in predefined categories.
- Many individuals already **mix multiple foundations** to achieve their perfect shade.
- Prior research has highlighted **biases in gender shade classification algorithms**, particularly affecting **darker skin tones**.
- Commercial makeup shade matching does not **account for intersectionality in skin tones**, creating gaps in representation.

## **Approach**
We divided our methodology into two main stages:

### **Stage 1: Computer Vision-Based Skin Tone Detection**
1. **Capture a well-lit portrait image**.
2. **Analyze skin tone using two detection algorithms**:
   - **Cheek Patch Detection Algorithm** (OpenCV Cascade Classifier)
   - **Face Segmentation Mask Algorithm** (Dlib’s 68 face landmarks)
3. **Match detected skin tone to the closest shade in the Makeup Shades Dataset** using **Euclidean Hex Distance**.

### **Stage 2: ShadeFusion Matching Algorithm**
1. Instead of selecting a single foundation shade, we **mix two shades within the same brand**.
2. Use **Euclidean Hex Distance** to measure how close the blended foundation shade is to the detected skin tone.
3. Iterate through different proportions (e.g., 0.1 increments) to find the optimal mix.
4. Introduce **pure black and white pigments** to improve accuracy for **darker skin tones** (ShadeFusion BW methodology).

## **Datasets Used**
- **Makeup Shades Dataset (Kaggle)**
  - Contains global foundation shade data categorized by **color range, brand, hex codes, hue, saturation, and lightness**.
  - Used for **algorithm training** and **bias detection**.

- **Monk Skin Tone Dataset (Google AI)**
  - Contains **1,570 images** representing **19 diverse skin tones**.
  - Used for **skin tone classification and equity measurement**.

## **Results & Interpretation**
### **Stage 1: Skin Tone Detection Performance**
| Algorithm | Overall Error Rate (Euclidean Hex Distance) |
|-----------|-------------------------------------------|
| **Cheek Patch Detection Algorithm** | 7.52 |
| **Face Segmentation Mask Algorithm** | 4.60 |

- The **Face Segmentation Algorithm** performed better due to **uniform skin tone detection**.
- Lighter skin tones showed **higher error rates**, indicating dataset bias.
- Side poses, facial hair, and lighting conditions affected accuracy.

### **Stage 2: ShadeFusion Matching Performance**
| Method | Error Distance |
|--------|--------------|
| **Best 1-1 Match** | 15.74 |
| **Best 2-1 Mix** | 1.41 |
| **ShadeFusion BW (Black & White Added)** | **Lowest Error** |

- **Mixing two foundation shades** significantly reduced error.
- Adding **pure black and white** to existing brand formulations **greatly improved matches for darker skin tones**.
- Our hypothesis that **ShadeFusion BW outperforms traditional shade matching** was confirmed.

## **Key Takeaways**
- **Bias in Makeup Industry**: Darker skin tones are underrepresented in foundation formulations.
- **Computer Vision Can Help**: Skin tone detection models can improve shade recommendations.
- **Color Theory Works**: Introducing **black and white pigments** increases inclusivity in foundation matching.
- **Future Work**: Expanding dataset diversity, incorporating real-world testing, and refining models for **better fairness in cosmetic AI applications**.

## **Study Limitations**
- **Data Bias**: Some datasets may not fully represent global skin tone distributions.
- **Lighting Variability**: Image capture conditions impact accuracy.
- **Subjectivity in Skin Tone Matching**: Individuals may perceive foundation matches differently.

## **Citations & References**
1. **Buolamwini, J. and Gebru, T. (2018).** Gender shades: Intersectional accuracy disparities in commercial gender classification. *PMLR*.
   - [Link](https://proceedings.mlr.press/v81/buolamwini18a.html?mod=article_inline)
2. **CIELAB Color Space**: [HunterLab](https://www.hunterlab.com/blog/what-is-cielab-color-space/)
3. **OpenCV Cascade Classifier**: [OpenCV Docs](https://docs.opencv.org/3.4/db/d28/tutorial_cascade_classifier.html)
4. **Dlib Facial Landmarks**: [PyImageSearch](https://pyimagesearch.com/2017/04/03/facial-landmarks-dlib-opencv-python/)
