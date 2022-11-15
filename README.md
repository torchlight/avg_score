# avg_score

Compute the average score of a DPC setup, given a solution set.
Takes into account tspins, quads, line clears, combos.
Doesn't currently take into account sd/hd points.

Usage:
1) Gather your solution set. Minimals, extra scoring solutions, whatever. Get them in glued fumen format. [fumen solutions]
2) precompute cover and nohold cover with sfinder
    Example commands:
    java -jar sfinder.jar cover -d 180 -p *p7 -t [fumen solutions]
    java -jar sfinder.jar cover -d 180 -p *p7 -t [fumen solutions] --hold avoid -o output/cover_nohold.csv
3) name them output/cover.csv and output/cover_nohold.csv and throw them in the same folder as this script
4) run script
    node avg_score.js

Hopefully it should output an average score.

Notes:
This assumes the solutions are valid and the cover.csv files were generated correctly. There's very little error handling.
There are a couple debugging console logs, comment them out if you wish.
For non 100% setups, adjust line ~425 to set how to handle fail queues. Default is to throw an error; alternatively, you can give that queue -3000.
Script works on solution queues without dupes. For solution queues with dupes, they can sometimes work; try by adjusting line ~151 and ~328. Default is to throw an error; alternatively, comment the else block out. This may allow the solution to be processed, depending on solution set.