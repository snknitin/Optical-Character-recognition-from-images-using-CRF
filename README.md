# Optical-Character-recognition-from-images-using-CRF
Exploring an approach that bridges computer vision and natural language processing by jointly modeling the labels of sequences of noisy character images that form complete words. This is a natural problem for chain-structured CRFs.The node potentials can capture
bottom-up information about the character represented by each image, while the edge potentials can capture
information about the co-occurrence of characters in adjacent positions within a word.

# Data:

The underlying data are a set of N sequences corresponding to images of the characters in individual words. Each word i consists of Li positions. For each position j in word i, we have a noisy binary image of the character in the that position. In this assignment, we will use the raw (binary) pixel values of the character images as features in the CRF. The character images are 20 × 16 pixels. We convert
them into 1 × 320 vectors. We include a constant bias feature along with the pixels in each image, giving a final feature vector of length F = 321. xijf indicates the value of feature f in position j of word i. The provided training and test files train_img<i>.txt and test_img<i>.txt list the character image xij on row j of file i as a 321-long space-separated sequence.1 The data files are in the column-major format. Given the sequence of character images xi = [xi1, ..., xiLi] corresponding to test word i, our goal is to infer the corresponding sequence of character labels yi = [yi1, ..., yiLi]. To reduce the computational complexity of exhaustive inference, we will use a limited set of characters corresponding to the 10 most frequently used characters in the English language: “etainoshrd”. There are thus C = 10 possible labels for each word position. The character labels for each training and test word are available in the files train_words.txt and test_words.txt. The figure below shows several example words along with their images.

# Model :
 The conditional random field model is a conditional model PW(yi|xi) of the sequence of class labels yi given the sequence of feature vectors xi that depends on a collection of parameters W .
