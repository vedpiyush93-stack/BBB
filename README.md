# Bounding Box Bonanza: can Claude do the volunteers' job?

On **903 handwritten manuscript pages** from the Zooniverse project
[Bounding Box Bonanza](https://www.zooniverse.org/projects/blicksam/bounding-box-bonanza), Claude, used out of the box
with no training and no example pages, is given the volunteers' job: **find every line of handwriting, read its words
and draw a tight box around it**. An expert who transcribed every page line by line is the answer key; the volunteers'
own boxes are the comparison.

<p align="center">
<a href="https://vedpiyush93-stack.github.io/BBB/"><b>Website</b></a> ·
<a href="https://vedpiyush93-stack.github.io/BBB/viewer/"><b>Browse all 903 pages</b></a> ·
<a href="https://vedpiyush93-stack.github.io/BBB/slides/"><b>See the slides</b></a>
</p>

![The method on one page: Kraken's rough lines, the page cut into strips, Claude's reading of a strip, the strips put back together, the sideways look, and the final boxes](docs/assets/method.jpg)

## The method in brief

1. A free line finder (Kraken) gives the usual gap between lines; the page is cut into overlapping strips of about 10 lines.
2. Claude reads each strip: where every line runs, and its words.
3. Two extra looks: writing turned sideways, and a close-up wherever Kraken saw a line Claude didn't report.
4. The lines are merged, and plain image processing (no AI) draws a tight box around each line's own ink.

## Results on 791 held-out pages

| | |
|---|---|
| Found (recall) | 92.8% of the expert's lines |
| Match (precision) | 92.3% of Claude's lines |
| Line score (F1) | 92.6 |
| Words | 94% of the expert's words |

Against the volunteers, on the 271 held-out pages they boxed (each box scored as the line along its bottom edge, with
the same F1): Claude 95.0 · best volunteer on each page 95.1 · typical volunteer 92.0 · volunteers' consensus 83.4.

## Work in progress

This repository holds the website only. The code, the notebook with every step and prompt, and the scripts to
reproduce the results will be released after review with the project team. No licence is granted yet: please ask
before reusing anything here.

The pages, the expert's transcriptions and the volunteers' boxes come from the Zooniverse projects Bounding Box Bonanza
and ACLS HTR Gold Standard Data and belong to their owners and to the archives that hold the originals. The page images
in the browser load directly from Zooniverse. Volunteers are never named.
