---
layout: post
comments: true
title: Akeneo | Protip - How to import assets with your product
category: akeneo
---

Did you know you can upload your products' assets with a classic produt import in akeneo? (even if you have lots of them)  
Yes? Well, you're one of the few (for now) :-D

When you think about it, an image or file attribute is "just" an attribute, so why won't we be able to import it?  

**It's a useful but not very known feature.**

For this example, we will use a standard (Akeneo connector) product import with a CSV file (job is *csv_product_import*) and upload a new image.

First, we define a basic CSV file :

```
sku;picture
13527420;monitor.png
```

Now, we have to upload the image with the CSV file, there are 2 solutions:


### If you have a small number of files

Check the sample import file, you'll notice that there's no specific path for the image, it means that it has to be at the same level as the CSV file.  
You can create any folder to classify your pictures and indicate it in the CSV, for example:

```
sku;picture
13527420;images/new/monitor.png
```

Now, we can create a zip with our CSV file and the picture, then we upload it directly in the job profile.

This picture sums up all these actions:

![Akeneo configuration product with media import](/assets/posts/akeneo-import-media-product/all.png){:width="700px"}


### If you have a lot of files *(you didn't see that coming right? :)*

First, upload your images to your webserver in a dedicated folder.  
Then in your CSV, reference those images (with the correct relative path).  
Finally, just drag and drop the CSV file, *do not make a heavy zip file*, Akeneo will find and import your images!  

*Notice: You will have the same behaviour, for both solutions, in specifying directly the file in the **File** properties of the batch job:*  

![Akeneo job configuration](/assets/posts/akeneo-import-media-product/job.png){:width="450px"}


Congratulations, the picture is now associated to our product!

![Akeneo product](/assets/posts/akeneo-import-media-product/product.png)

*Download the example zip file [here](/assets/posts/akeneo-import-media-product/product-media.zip).*
