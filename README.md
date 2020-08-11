# Stationary Wavelet Transform PyTorch 

```
J = 3
wave = 'db1'
mode='symmetric'

img_1 = pywt.data.camera()
img_2 = pywt.data.ascent()
img = np.stack([img_1, img_2], 0)

xx = torch.tensor(img).reshape(2,1,512,512).float()

sfm = SWTForward(J, wave, mode)
ifm = SWTInverse(wave, mode)

coeffs = sfm(xx)
recon = ifm(coeffs)

plt.subplot(2,2,1), plt.imshow(recon[0,0], cmap='gray')
plt.subplot(2,2,2), plt.imshow(recon[1,0], cmap='gray')

plt.subplot(2,2,3), plt.imshow(xx[0,0], cmap='gray')
plt.subplot(2,2,4), plt.imshow(xx[1,0], cmap='gray')
```

![Results](https://qgpmztmf.github.com/results.png)
