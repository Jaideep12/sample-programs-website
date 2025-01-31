---

title: Job Sequencing in Haskell
layout: default
date: 2022-04-28
last-modified: 2022-10-02

---

Welcome to the [Job Sequencing](https://sampleprograms.io/projects/job-sequencing) in [Haskell](https://sampleprograms.io/languages/haskell) page! Here, you'll find the source code for this program as well as a description of how the program works.

## Current Solution

{% raw %}

```haskell
module Main where

import System.Environment
import Text.Read
import Data.Map (Map)
import qualified Data.Map as Map

data Job = Job { profit :: Int, deadline :: Int } deriving (Show, Eq)

instance Ord Job where
  (Job p1 _) `compare` (Job p2 _) = p1 `compare` p2

type JobSequence = [Job]
type JobMapping = Map Int Job

-- Add up the profit of all Jobs in a JobMapping
maxProfit :: JobMapping -> Int
maxProfit = foldl (\total job -> total + profit job) 0 

-- Use greedy implementation to convert a JobSequence into a JobMapping that can be done by the deadline
iterateJobs :: JobSequence -> JobMapping
iterateJobs avail = iterate' avail Map.empty
  where iterate' []    complete = complete
        iterate' avail complete =
          let maxJob = maximum avail
              newAvail = rmJob maxJob avail
              is = [i | i <- [1..(deadline maxJob)], Map.notMember i complete]
              newComplete = if is /= []
                              then Map.insert (maximum is) maxJob complete
                              else complete
          in iterate' newAvail newComplete
        
-- Filter a specified Job from a JobSequence
rmJob :: Job -> JobSequence -> JobSequence
rmJob j js = filter (\x -> x /= j) js

-- Create a job from a tuple
job :: (Int, Int) -> Job
job (p, d) = Job p d

-- Create a JobSequence from a list of tuples
jobSequence :: [(Int, Int)] -> JobSequence
jobSequence []     = []
jobSequence (j:js) = job j : jobSequence js

headMaybe :: [a] -> Maybe a
headMaybe []     = Nothing
headMaybe (x:xs) = Just x

tailMaybe :: [a] -> Maybe [a]
tailMaybe []     = Nothing
tailMaybe (x:xs) = Just xs

-- Takes a list of values and returns a list of strings in the format "ONE_BASED_INDEX: VALUE"
printWithIndex :: (Show a) => [a] -> [[Char]]
printWithIndex = zipWith (\i x -> (show i) ++ ": " ++ (show x)) [1..]

-- Converts string in format "1, 2, 3" to a Maybe list of int
stringToListMaybe :: String -> Maybe [Int]
stringToListMaybe str = readMaybe $ "[" ++ str ++ "]" :: Maybe [Int]

main :: IO ()
main = do
  args <- getArgs
  let profit = headMaybe args >>= stringToListMaybe
  let deadline = tailMaybe args >>= headMaybe >>= stringToListMaybe
  let groups = zip <$> profit <*> deadline
  let jobs = fmap (jobSequence) groups
  case jobs of
    Nothing -> putStrLn "Usage: please provide a list of profits and a list of deadlines"
    Just n  -> putStrLn $ show $ maxProfit $ iterateJobs n
```

{% endraw %}

[Job Sequencing](https://sampleprograms.io/projects/job-sequencing) in [Haskell](https://sampleprograms.io/languages/haskell) was written by:

- Parker Johansen

If you see anything you'd like to change or update, [please consider contributing](https://github.com/TheRenegadeCoder/sample-programs).

## How to Implement the Solution

No 'How to Implement the Solution' section available. [Please consider contributing](https://github.com/TheRenegadeCoder/sample-programs-website).

## How to Run the Solution

No 'How to Run the Solution' section available. [Please consider contributing](https://github.com/TheRenegadeCoder/sample-programs-website).