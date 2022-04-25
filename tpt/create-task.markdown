---
permalink: /create-task
layout: tpt
title: Create Task
---

## Create Task

For my create task, I will be making a basic grade calculator. It will take assignment grades as input and output the final grade. This will use selection (option to remove lowest score), iteration (for loop to add scores and sum them), and sequencing. I can use lists to store the scores (collective data structures). It'll be written in python.

### Documentation


### Video
<iframe width="560" height="315" src="{{ site.baseurl }}/assets/videos/CreateTask.mp4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

#### Code

    test_scores = []

    # function to get the user's scores and store them into a list
    def generate_scores():
    # while loop to continue getting scores for an unspecified amount of time
        while True:
            score = input("Add a score: ")
            try: # try except to catch anyone trying to input a character or other invalid data types
                number_score = float(score)
                if number_score >= 0:
                    test_scores.append(number_score)
            except:
                print("Invalid input")

            print(f"Here are the scores you've inputted: {test_scores}")
            prompt = input("Would you like to keep adding scores? (Y/N)")
            if prompt.upper() == "N": # asks user if they want to continue; if not, exits the function
                return

    # helper function to get rid of lowest score
    def find_lowest_score(scores):
        min = 99999999 # set minimum score to a ridiculously high number at first
        min_index = -1 # first index out of range
        for i in range(len(scores)):
            if scores[i] < min: # if the score is less than the minimum, then that score becomes the new minimum
                min_index = i
                min = scores[i]
        return min_index

    # helper function to add all of the scores
    def get_sum(scores):
        sum = 0
        for num in scores:
            sum = sum + num
        return sum

    # driver function that combines all of the previous functions into one
    def driver():
        print("Welcome to the grade calculator! First, we need your test scores.")
        generate_scores()

        prompt = input("Would you like to remove the lowest score when calculating your grade? (Y/N)")
        if prompt.upper() == "Y":
            test_scores.pop(find_lowest_score(test_scores))

        print(f"Your final grade is {get_sum(test_scores)/len(test_scores)}.")

    if __name__ == "__main__":
        driver()

#### Responses

*3ai. Describes the overall purpose of the program*

The program is meant to calcuate one's final grade based off of their test score throughout the school term.

*3aii. Describes what functionality of the program is demonstrated in the video*

The video shows how the program works; the user inputs their scores into the terminal, the program takes those scores and puts them into a list, asks the user whether or not they want to exclude the lowest score, and outputs the final grade.

*3aiii. Describes the input and output of the program demonstrated in the video*

The input demonstrated in the video is the user inputting their scores. The video shows the user typing in their scores into the terminal. The output of the program is the final grade that is displayed at the end of the video.

*3bi. The first program code segment must show how data have been stored in the list.*

    # function to get the user's scores and store them into a list
    def generate_scores():
    # while loop to continue getting scores for an unspecified amount of time
        while True:
            score = input("Add a score: ")
            try: # try except to catch anyone trying to input a character or other invalid data types
                number_score = float(score)
                if number_score >= 0:
                    test_scores.append(number_score)
            except:
                print("Invalid input")

*3bii. The second program code segment must show the data in the same list being used, such as creating new data from the existing data or accessing multiple elements in the list, as part of fulfilling the program’s purpose.*

    # helper function to add all of the scores
    def get_sum(scores):
        sum = 0
        for num in scores:
            sum = sum + num
        return sum

    ...

    print(f"Your final grade is {get_sum(test_scores)/len(test_scores)}.")

*3biii. Identifies the name of the list being used in this response*

test_scores is the list being used.

*3biv. Describes what the data contained in the list represent in your program*

The data contained in the list represents the scores that the user inputted.

*3bv. Explains how the selected list manages complexity in your program code by explaining why your program code could not be written, or how it would be written differently, if you did not use the list.*

The list allows for scores to be added to one variable instead of having to create multiple, single variables that hold one score each. This would be extremely space intensive and inefficient to execute, so the list helps a lot in storing the scores.

*3ci. The first program code segment must be a student-developed procedure that:*
- [x] Defines the procedure’s name and return type (if necessary)
- [x] Contains and uses one or more parameters that have an effect on the functionality of the procedure
- [x] Implements an algorithm that includes sequencing, selection, and iteration

<br />

    # helper function to get rid of lowest score
    def find_lowest_score(scores):
        min = 99999999 # set minimum score to a ridiculously high number at first
        min_index = -1 # first index out of range
        for i in range(len(scores)):
            if scores[i] < min: # if the score is less than the minimum, then that score becomes the new minimum
                min_index = i
                min = scores[i]
        return min_index

*3cii. The second program code segment must show where your student-developed procedure is being called in your program.*

    prompt = input("Would you like to remove the lowest score when calculating your grade? (Y/N)")
    if prompt.upper() == "Y":
        test_scores.pop(find_lowest_score(test_scores))

*3ciii. Describes in general what the identified procedure does and how it contributes to the overall functionality of the program*

The identified procedure finds the lowest score in the given list of scores and returns the index of said score. This allows the program to remove the score before performing the final grade calculation.

*3civ. Explains in detailed steps how the algorithm implemented in the identified procedure works. Your explanation must be detailed enough for someone else to recreate it.*

The alogrithm identified starts by initializing two variables; the minimum score and the minimum score's index. The algorithm assigns these two variables ridiculous values (as opposed to something like 0) so that it's guaranteed to find at least one minimum value in the list. Then, the function iterates through each of the elements in the list. If it finds an element that is lower than the current minimum value, then it will set the minimum value to that new value and the index to the current index it is checking. At the end, the program will return the index of that minimum value.

*3di. Describes two calls to the procedure identified in written response 3c. Each call must pass a different argument(s) that causes a different segment of code in the algorithm to execute.*

First call:

    find_lowest_score([1, 2, 3, 4, 5, 6, 7])

Second call:

    find_lowest_score([95, 90, 89, 100, 93])

*3dii. Describes what condition(s) is being tested by each call to the procedure*

Condition(s) tested by the first call:

    if scores[0] < min: # only time that this if statement is true
        min_index = i
        min = scores[i]

Condition(s) tested by the second call:

    if scores[0] < min:
        min_index = i
        min = scores[i]

    if scores[1] < min:
        min_index = i
        min = scores[i]

    if scores[2] < min: # if statement is true three times (95, 90, 89), so the final min_index is set to 2 instead of 0
        min_index = i
        min = scores[i]

*3diii. Identifies the result of each call*

Result of the first call:
    0

Result of the second call:
    2