# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 8 steps. 

* Convert the image into gray scale.
* Blur the image using gaussian_blur.
* Compute the edges using canny.
* Selected the region of interests using region_of_interest().
* Compute the lane Lines using HoughLinesP() by repeating teaks the params to have the desired lines.
* Separate the lines into left and right by analyze its slope.
* Compute the lines that represent either left and right by first compute the average slope of the all lines that belong to either one side and the avg x and y coordinates. Then using slope and the avg x and y coord to find the corresponding lower and top coordinate using y = mx + b.
* plot the lines into the original image.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there aren't any edges found from a given image, then
my `avgLine` can result dividing 0 exception from :
```python
def avgLine(lines, width, height):
...
    x = sumx / (count * 2)
    y = sumy / (count * 2)
    m = sum /  (count)
...
```


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to have a guard against the divinding 0 errors.

Another potential improvement could be to refactor the code to be more readabe.
