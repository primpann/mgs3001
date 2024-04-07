# This progarm average test score. It asks the user for the number of students and the numbers of test score per student
import streamlit as st

st.title("Average Test Score Calculator")

# Get the number of students
num_students = int(st.number_input("How many students?: "))

# Get the number of test scores per student
num_test_scores = int(st.number_input("How many exams?: ",))

# Store the scores entered by the user
scores = []

# Collect scores for each student
for student in range(num_students):
    st.write('Student number', student + 1)
    student_scores = []
    for test_num in range(num_test_scores):
        while True:
            score = st.number_input(f"What is the score of test {test_num + 1} for student {student + 1}?: ",
                                    key=f"{student}-{test_num}")
            if 0 <= score <= 100:
                student_scores.append(score)
                break
            else:
                st.warning("Invalid score. Please enter a score between 0 and 100.")
    scores.append(student_scores)

# Calculate average scores
if st.button('Calculate'):
    st.write("Student\tAverage Score")
    for i, student_scores in enumerate(scores, start=1):
        average_score = sum(student_scores) / len(student_scores)
        st.write(f"{i}\t{average_score:.2f}")
