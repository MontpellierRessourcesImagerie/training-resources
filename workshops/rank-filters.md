# Rank filters

## Basic rank filters

<img src='https://g.gravizo.com/svg?
 digraph G {
    shift [fontcolor=white,color=white];
	"rank filters" -> awesome [label="  are"];
	"rank filters" -> minimum; 
	minimum -> erosion [label="  aka"];
	"rank filters" -> maximum; 
	maximum -> dilation [label="  aka"];
	"rank filters" -> median;
	"rank filters" -> "size" [label="  have"];
  }
'/>

### Activity: Explore rank filters on binary images

- Open image: xy_8bit_binary__two_spots_different_size.tif
- Explore how structures grow and shrink, using erosion and dilation

### Activity: Explore rank filters on grayscale images

- Open image: xy_8bit__two_noisy_squares_different_size.tif
- Explore how a median filter
	- removes noise
	- removes small structures
	- preserves egdes
- Compare median filter to mean filter of same radius


### Formative assessment

True or false? Discuss with your neighbour!

1. Median filter is just another name for mean filter.
2. Small structures can completely disappear from an image when applying a median filter.

Fill in the blanks, using those words: shrinks, increases, decreases, enlarges.

1. An erosion _____ objects in a binary image. 
2. An erosion in a binary image _____ the number of foreground pixels.
3. A dilation in a grayscale image _____ the average intensity in the image.
4. A dilation _____ objects in a binary image.


## Morphological opening and closing

<img src='https://g.gravizo.com/svg?
 digraph G {
    shift [fontcolor=white,color=white];
        "opening" -> "rank filter sequence" [label="  is"];
        "closing" -> "rank filter sequence" [label="  is"];
	"opening" -> "removes small structures";
	"closing" -> "fills small gaps";
  }
'/>

```
opening( image ) = dilation( erosion( image ) )
```

```
closing( image ) = erosion( dilation( image ) )
```


### Activity: Explore opening and closing on binary images

- Open image: xy_8bit_binary__for_open_and_close.tif
- Explore effects of morphological closing and opening:
	- closing can fill holes
	- closing can connect gaps
	- opening can remove thin structures 


### Formative assessment

TODO


## Top hat filter for local background subtraction

<img src='https://g.gravizo.com/svg?
 digraph G {
    shift [fontcolor=white,color=white];
	"tophat" -> "rank filter sequence"; 
	"tophat" -> "local background subtraction";
  }
'/>


```
tophat( image ) = image - opening( image, r ) =  image - dilation( erosion( image, r), r )
```


### Activity: Explore tophat filter

- Open image: xy_8bit__spots_local_background.tif
- Use a tophat filter to remove local background

## Activity: Implement a tophat filter

- Devise code implementing a tophat filter, using minimum and maximum filters

## Activity: Explore tophat filter on biological data

- Open image: xy_16bit__autophagosomes.tif 
- Appreciate that you cannot readliy segment the spots.
- Use a tophat filter to remove local background.
- Threshold the spots in the tophat filtered image.

## Activity: Explore tophat fiter on noisy data

- Open image: xy_8bit__spots_local_background_with_noise.tif 
- Use topHat filter to remove local background
- Appreciate that noise poses a challenge to the tophat filter


### Formative assessment

TODO


## Median filter for local background subtraction

<img src='https://g.gravizo.com/svg?
 digraph G {
    shift [fontcolor=white,color=white];
	"median" -> "local background" [label="  approximates"];
	"median" -> "radius" -> "> object width";
	"radius" -> "< spatial background frequency";
  }
'/>


```
median_based_background_correction = image - median( image, r)
```



### Activity: Implement median based background subtraction

- Write code to implement a median based background subtraction


### Activity: Explore median filter for local background subtraction

- Open images: 
	- xy_8bit__spots_local_background.tif 
	- xy_8bit__spots_local_background_with_noise.tif
	- 
- Use topHat filter to remove local background
- Devise code to implement a tophat filter using basic functions

### Formative assessment

TODO



## Learn more

- https://imagej.net/MorphoLibJ#Grayscale_morphological_filters


