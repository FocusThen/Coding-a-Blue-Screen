# Coding-a-Blue-Screen

### Orginal İmage
![midoria](https://user-images.githubusercontent.com/47830409/63759013-70514e80-c8c5-11e9-92a2-86ac249e723a.jpg)

### Cv2 reads Midoria BGR

```sh
image = cv2.imread('midoria.jpg')
```  
![BGRMidoria](https://user-images.githubusercontent.com/47830409/63759146-b0b0cc80-c8c5-11e9-8f77-8d5f93709012.jpg)
  - We need change to RGB
```sh
rgb_image_copy = cv2.cvtColor(image_copy, cv2.COLOR_BGR2RGB)
```

### Mask

```sh
lower_blue = np.array([0, 0, 100])
upper_blue = np.array([50, 90, 255])
mask = cv2.inRange(rgb_image_copy, lower_blue, upper_blue)
```
![MaskMidoria](https://user-images.githubusercontent.com/47830409/63759673-95928c80-c8c6-11e9-9185-0866ab34bd16.jpg)

### Masked image

```sh
masked_image = np.copy(rgb_image_copy)
masked_image[mask != 0] = [0,0,0]
```
![MaskedMidoria](https://user-images.githubusercontent.com/47830409/63759723-a8a55c80-c8c6-11e9-8cc8-7db4e2459ddb.jpg)

### Making background

```sh
background_image = cv2.imread('space.jpg')
background_image = cv2.cvtColor(background_image, cv2.COLOR_BGR2RGB)

crop_backgroundimg = background_image[0:720 , 0:1280]
crop_backgroundimg[mask == 0] = [0, 0, 0]
```
![background](https://user-images.githubusercontent.com/47830409/63759753-b5c24b80-c8c6-11e9-92c5-934a0ca3d2da.jpg)

### Complite the image

```sh
complete_image = crop_backgroundimg + masked_image
```

![completeimage](https://user-images.githubusercontent.com/47830409/63759768-bd81f000-c8c6-11e9-8eb5-39a674df972b.jpg)

