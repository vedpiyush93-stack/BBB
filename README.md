# Bounding Box Bonanza: can Claude do the volunteers' job?

On **903 handwritten manuscript pages** from the Zooniverse project
[Bounding Box Bonanza](https://www.zooniverse.org/projects/blicksam/bounding-box-bonanza), Claude, used out of the box
with no training and no example pages, is given the volunteers' job: **find every line of handwriting, read its words
and put a box around it**. An expert who transcribed every page line by line is the answer key; the volunteers' own
boxes are the comparison.

<p align="center">
<a href="https://vedpiyush93-stack.github.io/BBB/"><b>Website</b></a> ·
<a href="https://vedpiyush93-stack.github.io/BBB/viewer/"><b>Browse all 903 pages</b></a> ·
<a href="https://vedpiyush93-stack.github.io/BBB/slides/"><b>See the slides</b></a>
</p>

![The method on one page: Kraken's lines and outlines, the page with Kraken's numbered lines that Claude reads, Claude's lines and words, and the boxes](docs/assets/method.jpg)

## The method in brief

1. **Kraken finds the lines.** A free line finder that can't read marks every line of writing and draws an outline
   around it.
2. **Claude reads the page, in one call.** It sees the page with Kraken's lines numbered in red and writes out every
   line's words, saying which red line(s) each sits on.
3. **Boxes, no AI.** Each box is the smallest rectangle around Kraken's outline of a line; boxes that overlap meet
   halfway.

Kraken alone scores 80.7 (line score) and can't read; with Claude's one answer per page, which drops Kraken's junk
lines, joins its broken pieces, splits lines that run across two pieces of writing, adds the lines it missed and reads
every word, the score is 92.5.

## Results on 791 held-out pages

| | |
|---|---|
| Found (recall) | 90.5% of the expert's lines |
| Match (precision) | 94.6% of Claude's lines |
| Line score (F1) | 92.5 |
| Words | 94.0% of the expert's words (3.8 letter errors per 100) |
| Boxes | 82% of the expert's lines sit inside one box; 86% of boxes hold exactly one line |

Against the volunteers, on the 271 held-out pages they boxed (each box scored as the line along its bottom
edge, with the same F1): Claude 94.1 · best volunteer on each page 95.1 · typical volunteer 92.0 ·
volunteers' consensus 83.4.

## Work in progress

This repository holds the website only. The code, the notebook with every step and prompt, and the scripts to
reproduce the results will be released after review with the project team. No licence is granted yet: please ask
before reusing anything here.

The pages, the expert's transcriptions and the volunteers' boxes come from the Zooniverse projects Bounding Box Bonanza
and ACLS HTR Gold Standard Data and belong to their owners and to the archives that hold the originals. The page images
in the browser load directly from Zooniverse. Volunteers are never named.
