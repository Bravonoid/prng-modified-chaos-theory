# Pseudorandom Number Generators: Modified Chaos Theory

This is a repository of pseudorandom number generators (PRNGs) that use modified chaos theory to generate random numbers. The generators are written in Python and are designed to be easy to understand and modify. The generators are not intended to be used for cryptography or other security purposes.

## Proposed Generators

### Overview

In this method, we will use the pixel values of a grayscale image as a seed. Through these pixel values, we will calculate the values that will be used to compute the next pseudorandom value. These values are:

- The pixel value at position (x, y) in the grayscale image.
- The norm value of the pixel matrix centered at position (x, y) in the grayscale image (with a matrix size determined by the `kernel_size` parameter) that will be used as the rate of change.
- The decimal value of the previous pseudorandom result.

Then, we will calculate the next pseudorandom value using the following formula:

![PRNG Formula](https://latex.codecogs.com/png.image?\dpi{110}\bg{black}\text{PRNG}_{i}&space;=&space;\text{Rate}_{i}&space;\times&space;\text{Pixel}_{i}&space;\times&space;\text{LatestRandomDecimal}_{i})

![PRNG Formula](<https://latex.codecogs.com/png.image?\dpi{110}\bg{black}\text{PRNG}_{i}&space;=&space;\text{Rate}_{i}&space;\times&space;\text{Pixel}_{i}&space;\times&space;(\text{PRNG}_{i-1}&space;-&space;\text{round(PRNG)}_{i-1})>)

This will produce a different pseudorandom value every time it is run, as the pixel values of the grayscale image will change every time it is run and the norm value of the pixel matrix will also change every time it is run.

### Norm of Pixel Matrix

The norm of a pixel matrix is the sum of the absolute values of the pixel values in the matrix. The norm of a pixel matrix is used to calculate the rate of change of the pseudorandom value. The norm of a pixel matrix is calculated using the following formula:

![Norm Formula](https://latex.codecogs.com/png.image?\dpi{110}\bg{black}\text{Norm}_{i}&space;=&space;\sum_{j=1}^{n}&space;\left&space;|&space;\text{Pixel}_{i}&space;\right&space;|)

### Latest Random Decimal

The latest random decimal is the decimal value of the previous pseudorandom value. The latest random decimal is used to calculate the next pseudorandom value. The latest random decimal is calculated using the following formula:

![Latest Random Decimal Formula](<https://latex.codecogs.com/png.image?\dpi{110}\bg{black}\text{LatestRandomDecimal}_{i}&space;=&space;\text{PRNG}_{i-1}&space;-&space;\text{round(PRNG)}_{i-1}>)

### Pseudorandom Value

The pseudorandom value is calculated using the following formula:

![PRNG Formula](https://latex.codecogs.com/png.image?\dpi{110}\bg{black}\text{PRNG}_{i}&space;=&space;\text{Rate}_{i}&space;\times&space;\text{Pixel}_{i}&space;\times&space;\text{LatestRandomDecimal}_{i})

![PRNG Formula](<https://latex.codecogs.com/png.image?\dpi{110}\bg{black}\text{PRNG}_{i}&space;=&space;\text{Rate}_{i}&space;\times&space;\text{Pixel}_{i}&space;\times&space;(\text{PRNG}_{i-1}&space;-&space;\text{round(PRNG)}_{i-1})>)

## Parameters

Here are the parameters used in this method:

- `kernel_size`: The size of the matrix used to calculate the norm value of the pixel matrix centered at position (x, y) in the grayscale image (int).
- `seed`: The image to be used as the seed (numpy array).
- `n`: The number of pseudorandom values to be generated (int).
- `alpha`: The value used as the initial value of latest_decimal_number (float). The default value is 0.5.

## Results

Here are the results of the proposed generators using parameters:

- `kernel_size`: 3
- `seed`: 'majestic.png'
- `n`: 100
- `alpha`: 0.5

![](./majestic.png)

### n = 100

Number of Pseudorandom Values: 100

- Number of 1s: 45
- Number of 0s: 55
- Ratio of 1s to 0s: 0.8181818181818182

### n = 1000

Number of Pseudorandom Values: 1000

- Number of 1s: 481
- Number of 0s: 519
- Ratio of 1s to 0s: 0.9267822736030829

### n = 10000

Number of Pseudorandom Values: 10000

- Number of 1s: 4924
- Number of 0s: 5076
- Ratio of 1s to 0s: 0.9700551615445232

### n = 100000

Number of Pseudorandom Values: 100000

- Number of 1s: 49918
- Number of 0s: 50082
- Ratio of 1s to 0s: 0.9967253703925562

### n = 1000000

Number of Pseudorandom Values: 1000000

- Number of 1s: 500163
- Number of 0s: 499837
- Ratio of 1s to 0s: 1.0006522126213147
