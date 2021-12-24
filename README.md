# Laboratory4ImageProcessing

## Здесь мы нормализуем изображение
def normalize_image(img):
    norm_image = cv.normalize(
        img, None, alpha=0, beta=1, norm_type=cv.NORM_MINMAX, dtype=cv.CV_32F)
    return norm_image
    
## мы определяем фильтр Габора и применяем его
def Gabor_filtering(img, ker_size, si, t, l, angle):
    kernel = cv.getGaborKernel((ker_size,ker_size),si,t,l,angle)
    out =  cv.filter2D(img,-1,kernel)
    return out
    
def apply_gabor_filter(img):
    angles = [0,20,40,60,80,90]
    out = []
    for a in angles:
        res = Gabor_filtering(img, 15, 7, 11, 3, a)
        out.append(res)
    return out,angles

##   - Нормализация и преобразование в int8 (adaptiveThreshold работает только с int8 - Бинаризация - Использование медианного размытия

## Результаты
![finger1](https://user-images.githubusercontent.com/65180398/147357451-130d3eda-c5c0-4191-b72e-440efd8da4a2.png)
![finger2](https://user-images.githubusercontent.com/65180398/147357675-fc44a7e3-6855-4038-a62b-5486ddb8dc8a.png)
![finger3](https://user-images.githubusercontent.com/65180398/147357694-6305e94c-3616-4df2-9a28-04e344145422.png)
![finger4](https://user-images.githubusercontent.com/65180398/147357733-f7051d15-7d3b-45b0-857e-bf972d42a0ee.png)
![finger5](https://user-images.githubusercontent.com/65180398/147357753-b4e07409-0fec-459c-8f02-9e707589cdd0.png)
![finger6](https://user-images.githubusercontent.com/65180398/147357793-b167a235-5ceb-499f-bfea-7c9f84f7191b.png)
