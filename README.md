# WSQ-Encoder-Decoder

## introduction
The **Wavelet Scalar Quantization algorithm (WSQ)** is a compression algorithm used for gray-scale fingerprint images. It is based on wavelet theory and has become a standard for the exchange and storage of fingerprint images. WSQ was developed by the FBI, the Los Alamos National Laboratory, and the National Institute of Standards and Technology (NIST).

## Sources
An open-source WSQ image encoder/decoder for Android based on [NBIS](https://www.nist.gov/services-resources/software/nist-biometric-image-software-nbis) v5.0.0.

## Usage

Encoding an image:
```kotlin
val portrait: InputStream = context.assets.open("portrait.png")
val bitmap: Bitmap = BitmapFactory.decodeStream(portrait)

// higher-quality encode
val wsqData: ByteArray = WSQEncoder(bitmap)
                        .setBitrate(WSQEncoder.BITRATE_5_TO_1)
                        .encode()

// lower-quality encode
val wsqData: ByteArray = WSQEncoder(bitmap)
                        .setBitrate(WSQEncoder.BITRATE_15_TO_1)
                        .encode()
```

Decoding an image:
```kotlin
val bitmap: Bitmap = WSQDecoder.decode(wsqData).bitmap
imgView.setImageBitmap(bitmap);
```


## Set up
Add dependency to your `build.gradle`
```groovy
implementation("fr.sabry.wsq:wsq:1.1.1")
```
