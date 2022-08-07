<p align="center">
  <img alt="🔎CSI_with_Blind_Image_Deconvolution" src="https://user-images.githubusercontent.com/62103572/183286575-b9140063-6c41-4428-ba8a-8fb874a84be2.png">
  <img alt="GitHub commit activity" src="https://img.shields.io/github/commit-activity/y/EliaFantini/CSI-using-Blind-Image-Deconvolution-and-Frank-Wolfe-algorithm">
  <img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/EliaFantini/CSI-using-Blind-Image-Deconvolution-and-Frank-Wolfe-algorithm">
  <img alt="GitHub code size" src="https://img.shields.io/github/languages/code-size/EliaFantini/CSI-using-Blind-Image-Deconvolution-and-Frank-Wolfe-algorithm">
  <img alt="GitHub repo size" src="https://img.shields.io/github/repo-size/EliaFantini/CSI-using-Blind-Image-Deconvolution-and-Frank-Wolfe-algorithm">
  <img alt="GitHub follow" src="https://img.shields.io/github/followers/EliaFantini?label=Follow">
  <img alt="GitHub fork" src="https://img.shields.io/github/forks/EliaFantini/CSI-using-Blind-Image-Deconvolution-and-Frank-Wolfe-algorithm?label=Fork">
  <img alt="GitHub watchers" src="https://img.shields.io/github/watchers/EliaFantini/CSI-using-Blind-Image-Deconvolution-and-Frank-Wolfe-algorithm?label=Watch">
  <img alt="GitHub star" src="https://img.shields.io/github/stars/EliaFantini/CSI-using-Blind-Image-Deconvolution-and-Frank-Wolfe-algorithm?style=social">
</p>


This project applies the Frank-Wolfe's algorithms to solve the problem of Blind Image deconvolution, in order to deblur the image of a license plate of which it's impossible to read the digits. Such algorithm would be helpful for a potential Crime Scene Investigation (CSI) where the photo of a criminal's car has been taken but the license plate is blurred  and unreadable. 

Deblurring is an instance of the blind deconvolution problem: given two unknown vectors **x**, **w**, we observe their circular convolution **y = w ∗ x**. Blind deconvolution seeks to separate w and x, given y. The operative word blind comes from the fact that we do not have much prior information about the signals.

For a more detailed explanation, please read *Exercise instructions.pdf*, it contains also some theoretical questions answered in *Answers.pdf* (handwritten). 

The project was part of an assignment for the EPFL course [EE-556 Mathematics of data: from theory to computation](https://edu.epfl.ch/coursebook/en/mathematics-of-data-from-theory-to-computation-EE-556). The backbone of the code structure to run the experiments was already given by the professor and his assistants, what I had to do was to implement the core theoretical concepts to actually make the experiments work. Hence, every code file is a combination of my personal code and the code that was given us by the professor.

## Author
-  [Elia Fantini](https://github.com/EliaFantini)

## Why Frank-Wolfe

The  Blind Image Deconvolution problem described above can be reformulated as a constrained optimization problem. Constrained optimization can be solved with proximal methods that require a projection of the solution back into the constrained set. Such projection though can be computationally expensive and not scalable. For this reason, the Frank-Wolfe algorithm might be preferable.

The Frank–Wolfe algorithm is an iterative first-order optimization algorithm for constrained convex optimization. In each iteration, the Frank–Wolfe algorithm considers a linear approximation of the objective function, and moves towards a minimizer of this linear function (taken over the same domain).

In this project's problem, the constrained set is the set of *m***p* matrices with a nuclear norm smaller than *k*. The projection in such set can be obtained using the Singular Value Decomposition, while the lmo (linear minimization oracle) for Frank-Wolfe only requires the computation of the left and right singular vectors that correspond to the largest singular value of the matrices.

By running **projection.py** or the related jupyter notebook and by doing the same with **lmo.py** (or related notebook), I get the following table that shows how Frank-Wolfe (LMO) is much faster and more scalable than the projection for this use case:
<p align="center">
<img width="800" alt="Immagine 2022-08-07 140936" src="https://user-images.githubusercontent.com/62103572/183289866-0ae6286b-7d2f-4a98-9334-0760619ed654.png">
<img width="800" alt="Immagine 2022-08-07 140947" src="https://user-images.githubusercontent.com/62103572/183289877-bf0f6caa-44ed-4fc9-9dbc-d394cfc3cd68.png">

## Results
By applying Fronk-Wolfe to solve the  Blind Image Deconvolution problem and running **Test_deblur.py** or the realted jupyter notebook, we can see that the license plate is **J209LTL**. The optimization makes the license plate readable from the 10th/15th iteration already, in the image I chose randomly the 33rd and the 34th iteration, they're not the most readable.
<p align="center">
<img width="auto" alt="Immagine 2022-08-07 141522" src="https://user-images.githubusercontent.com/62103572/183290088-fd892771-b240-400c-9fcf-08745369e32b.png">
</p>

## How to install and reproduce results
Download this repository as a zip file and extract it into a folder
The easiest way to run the code is to install Anaconda 3 distribution (available for Windows, macOS and Linux). To do so, follow the guidelines from the official
website (select python of version 3): https://www.anaconda.com/download/

Additional package required are: 
- matplotlib
- scipy
- jupyter notebooks (optional)

To install them write the following command on Anaconda Prompt (anaconda3):
```shell
cd *THE_FOLDER_PATH_WHERE_YOU_DOWNLOADED_AND_EXTRACTED_THIS_REPOSITORY*
```
Then write for each of the mentioned packages:
```shell
conda install *PACKAGE_NAME*
```
Some packages might require more complex installation procedures. If the above command doesn't work for a package, just google "How to install *PACKAGE_NAME* on *YOUR_MACHINE'S_OS*" and follow those guides.

Finally, run **lmo.py**, **projection.py** and **Test_deblur.py** or the realted jupyter notebooks. 
```shell
python lmo.py
python projection.py
python Test_deblur.py
```

## Files description

- **code/dataset**: folder containing the dataset to run the experiments

-  **code/projection.py**: script to be run in order to test the projection's execution time and scalability (the jupyter notebook with the same name does the same).

-  **code/lmo.py**: script to be run in order to test the Frank-Wolfe's execution time and scalability (the jupyter notebook with the same name does the same).

-  **code/Test_deblur.py**: script to perform the Blind Image Deconvolution (the jupyter notebook with the same name does the same).

- **Answers.pdf**: pdf with the answers and plots to the assignment of the course

- **Exercise instructions.pdf**: pdf with the questions of the assignment of the course

## 🛠 Skills
Python, Matplotlib, Scipy, Jupyter notebooks. Machine learning, constrained optimization algorithms implementation, constrained nuclear norm projection, singular value decomposition, linear minimization oracle (LMO), Frank-Wolfe, Blind Image Deconvolution.

## 🔗 Links
[![portfolio](https://img.shields.io/badge/my_portfolio-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://github.com/EliaFantini/)
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/-elia-fantini/)


