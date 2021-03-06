## Dehazing using Color-lines
This repository contains an open source implementation of [Fattal's algorithm for dehazing](https://www.cse.huji.ac.il/~raananf/projects/dehaze_cl/). 
It is meant as an accessible implementation with low complexity and ample documentation that can be used as an aid for studying the algorithm.   
  
For a compiled implementation, consider the implementations by [Ekesium](https://github.com/ekexium/dehazing-using-color-lines) and [Tomlk](https://github.com/Tomlk/Dehazing-with-Color-Lines) (also pixel-wise inference, but in scala and C++). Alternatively, consider writing a vectorized implementation. 

![Current result](images/dehaze.gif)

## How to Use 
Use a venv and install the required packages by running `pip install -r requirements.txt`.    
Execute `python dehaze.py` to dehaze `images/bricks.png`. 

## Example output
![example output](images/example.png)
<img src="images/fattal_result.png" width="35%">.

To find other images with a given airlight vector, see the paper's [result page](https://www.cse.huji.ac.il/~raananf/projects/dehaze_cl/results/).

## File structure 
| Name                    | Purpose                                                                           |
|-------------------------|-----------------------------------------------------------------------------------|
| dehaze.py               | Main function                                                                     |
| ransac.py               | RANSAC algorithm for evaluating color-line hypotheses                             |
| window.py               | A windowing class for concise tiling                                              |
| color_line.py           | Functions for evaluating color-line validity                                      |
| constants.py            | All constants and thresholds (comments note where it deviates from Fattal)        |
| linear_interpolation.py | Linear interpolation of the transmission image                                    |
| markov_random_field.py  | Markov random field interpolation and smoothing functions (autograd optimization) |
| recover.py              | Recovers the dehazed pixel values given the estimated transmission map            |


## TODO 
* Implement [automatic airlight recovery](https://www.cse.huji.ac.il/~raananf/projects/atm_light/)
