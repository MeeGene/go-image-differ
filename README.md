# go-image-differ

This library is from github.com/olegfedoseev/image-diff

本库来自 github.com/olegfedoseev/image-diff

The difference is that the go-image-differ obtains the difference between the two images

不同在于，go-image-differ 获取的是两张图片差异的内容

# How to get and use

```
go get -u github.com/MeeGene/go-image-differ
```

And in you code:

```

    import "github.com/MeeGene/go-image-differ"

    diff, percent, err := diff.CompareFiles("test-only-text.png", "test-text-number.png")
    if percent > 0.0 {
        snapshotImageRect := diff.Bounds()
        newImage := image.NewRGBA(snapshotImageRect)
        draw.Draw(newImage, snapshotImageRect, diff, snapshotImageRect.Min, draw.Over)

        newFileName := strconv.Itoa(int(time.Now().Unix()))
        newImageFile, err := os.Create(newFileName + ".png")
        if err != nil {
            fmt.Println(err)
        }

        png.Encode(newImageFile, newImage)
        newImageFile.Close()
    }
```