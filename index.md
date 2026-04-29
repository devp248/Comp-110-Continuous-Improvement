---
# Do not edit the text between these lines!
layout: default
---

# Should COMP110 Record Its Lectures?

This is a continuous improvement project exploring whether recording all COMP110 lectures would create real value for students based on responses to the anonymous course survey.

## The Idea

**The course should record all lectures so students can go back and review material they may have missed during class and study at their own pace.**

This idea is aimed primarily the benefit students enrolled in COMP110, but it also has potential value for instructional staff because of improved performance, fewer questions, and better learning outcomes for studetns. 

I picked this idea over the others I brainstormed because it had the clearest direct data point in the survey which was the `add_livestream` question and because i thoguht that the data would support it and it would be relatively easy to implement. 

## Summary of Analysis

I started by loading the survey using `read_csv_rows` and converting it into a column-oriented table with `columnar`, then previewed the first few rows with `head` to make sure the data looked right.

To investigate the idea, I focused on the `add_livestream` column. This column asks students how strongly they agree that lectures should be available outside of class on a 1–7 scale. I used `select` to isolate that column, `count` to tally how many students chose each rating, and a custom `sort_counts` helper function to put the ratings in order from 1 to 7.

I then visualized the results three ways using `seaborn`. First, a bar chart of the overall response distribution. Then two scatterplots cross-referencing `add_livestream` against two other variables which were `understanding` and `valuable` to check whether the demand for recordings was concentrated among struggling students or was broader.

## Findings

### Chart 1: Overall Student Support for Lecture Recordings

A clear majority of students agree that lectures should be available outside of class. The distribution is heavily skewed to the right. Over 200 students gave the highest rating (7), and the top three ratings (5, 6, 7) together account for the vast majority of responses. 

<img src="/Comp-110-Continuous-Improvement/static/images/livestream_bar.png" alt="Bar chart showing student responses to add_livestream question, heavily skewed toward agreement" width="600"/>

### Chart 2: Lecture Recording Support vs. Understanding of the Material

If the idea were primarily helping struggling students then we would expect students who have low understanding to want recordings more than students who have higher understanding. The scatterplot doesn't show that pattern however. Students at every level of understanding gave high `add_livestream` ratings. 

<img src="/Comp-110-Continuous-Improvement/static/images/livestream_vs_understanding.png" alt="Scatterplot of add_livestream vs understanding, showing no strong relationship" width="600"/>

### Chart 3: Lecture Recording Support vs. Perceived Course Value

The same thing applies when comparing `add_livestream` against `valuable`. Whether students see the course as deeply valuable or only somewhat valuable, the desire for recorded lectures is still high across the board. This plot suggests that wanting recordings is not related to whether a student is enthusiastic about the course or skeptical of it.

<img src="/Comp-110-Continuous-Improvement/static/images/livestream_vs_valuable.png" alt="Scatterplot of add_livestream vs valuable, showing no strong relationship" width="600"/>

## Conclusion

Overall, the data somewhat supports the idea of recording lectures but further analysis would be needed to fully confirm if this implementation would be supported. The bar chart showed that many students rated add_livestream on the higher end (around 5–7). This suggests that a large portion of the class is interested in having lectures available outside of class indicating that recording lectures could be useful for students who want to review material or need more flexibility.

However, the scatterplots comparing add_livestream with understanding and valuable did not show a strong relationship. Students at all levels of understanding and perceived course value had a wide range of opinions on lecture recordings. This means that while many students want recordings, it is not necessarily tied to how well they understand the material or how valuable they find the course.

Based on these findings, I would still recommend recording lectures because it appears to benefit a wide range of students, not just those who are struggling. A possible extension of this idea would be to track how often students actually use recorded lectures and whether it improves their performance or understanding over time. I think it would also be helpful to know data beyond just the classes this semester, having data from years past would also help make better conclusions. 

One potential trade-off of implementing this is that some students might attend class less if recordings are available, which could reduce in-person engagement. Additionally, recording and managing lectures could require extra time or resources from instructors. Despite this, the overall demand shown in the data suggests that recording lectures would create value for many students and testing how having recorded lectures available influences student performance over time would be a great way to test this.  