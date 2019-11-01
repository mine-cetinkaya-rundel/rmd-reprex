# rmd-reprex

## Motivation

Most intro data science / stats courses use an Rmd based workflow almost entirely or at 
least for the first big chunk of the course. There are also various workshops that 
adopt this workflow entirely. 

Going from an error in an Rmd file to a reprex in an R script is not an easy task for 
novice learners, so it would be nice to offer them a pathway to developing reprexes 
as they're learning R using (mostly, or entirely) Rmd files for their work.

## Example: `hw1.Rmd`

A sample analysis with two chunks with that requires reprexes.

1. Chunk: `calculate-mean-sw` -- No error but not what I want
2. Chunk: `plot-ratios` -- Error

## Notes

- There is a `reprex selection` addin but it is not context aware so doesn't 
see previous chunks in an Rmd.

- Each of the question chunks are preceded by some chunks that are needed to 
create a reprex and some that are not. So the question asker needs to get 
rid of unneeded chunks.
  - But we want to be careful about asking people to delete stuff from their Rmd.
  
## Proposal: `reprex rmd` addin

1. Select what Rmd file you want to create a reprex from:
  - User to select using a browser window that starts at the current working directory
  - Suppose file is called `hw1.Rmd`
  
--> This creates an Rmd file called `hm1-reprex.Rmd` where 
`output: reprex` (which means it knits and it copies to clipboard)

2. Select from a list of all chunks in the document using a `radioButtons()` 
*only* the chunk you have a question about first. 

--> This adds the selected chunk to `hw1-reprex.Rmd` and knits `hw1-reprex` 
with `knitr::opts_chunk$set(error = TRUE)`.

3. Prompt asking whether this is the reprex they wanted:
  * Yes -- select venue, copy to clipboard, and done
  * No -- this is likely because previous chunks needed to be included to 
  achieve the original error
  
4. If No is selected for 3 - Select any chunks from `hw1.Rmd` that should also 
be added to the reprex using `checkboxInput()` and 3<->4 until happy.

## Anticipated questions

Q: Is this really easier than recommending these stages to students?
A: Yes, making copies and selectively adding chunks is not easy. If it were, 
they'd have just as easy a time making reprexes as is.

Q: Can we trust the question asker to make the right decision on stage 3?
A: Not sure, but it'll be a learning experience for them either way

## Caveats

- This might work nicely for Question 1 (there's an error) but how about 
for Question 2 (code runs, just doesn't yield what you want)

## Unclear

- Can we show a sneak preview of the chunk's contents during selection? 
  - I think so...
- Do we leave chunks as separate chunks or combine them all? 
  - I think leave as is, don't combine.
- Can we detect the use of `<-` in the last chunk of the reprex and advise 
printing out the result?
  - I'm not sure if this is generalizable, but it's a mistake I see regularly.


