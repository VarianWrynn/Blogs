## Some Telephone Interview Questions

> Some Telephone Interview Questions for C++C# Software Enginers

- What is a Garbage Collector in C# (what does it do).
- Are the objects automatically GC-ed in C#? If not, why/how?
- Are the structs automatically GC-ed in C#?
- Tell me the difference between stack and heap (memory management)
- What is a virtual [destructor](https://helloacm.com/constructor-and-destructor-in-python-classes/) in C++?
- How do you run two methods in parallel in C#?
- If two methods both increment a variable, is there a problem (is the value higher or lower) and how to fix it?
- How do you implement a function that takes a byte value and return true if its most-significant-bit is set?
- What is the difference between *as* and *is* in C#?



### SOME ANSWERS

You can use *Parallel.Invoke* or *Task.Factory.StartNew* *and* *Task.WaitAll* to run two methods in parallel.

structs are value-types so they are automatically GC-ed in C#.

Primitive data types like *int* live in stack while objects are normally in heap.

```C#
inline bool check(byte v) {
  return v & 0b10000000; 
}
```

You need to lock the variables when multiple threads write to them at the same time – race conditions.

–EOF ([The Ultimate Computing & Technology Blog](https://helloacm.com/)) —

## C# Questions from Job Agency

I talked to a job agency and surprisingly the agency asked me 10 questions about C#. I think it is a bit surprising because this is the first time I got technical questions on the telephone from a job recruiting agency and as you can understand, these questions are not hard. It is designed for 2 minute screening in case you know nothing about C#.

- How do you declare a nullable integer in C#?
- How do you handle a [exception](https://helloacm.com/null-reference-exception-due-to-null-string-in-c/)?
- Can you overload two methods that have different return type?
- What does the overload keyword mean?
- What keyword allows the class attributes to be only accessed in current class and its derived class.
- What keyword allows the method to be overridden in derived class?
- Is integer value type or reference type?
- where can you deploy assemblies of your application on the machine? – I am not sure I get this right.
- When you declare an object in a method, where is it stored, heap or stack?
- When a variable goes out of scope, what would happen?

Please write your answers in the comment.

–EOF ([The Ultimate Computing & Technology Blog](https://helloacm.com/)) —



## Last Minute Tips before Phone Interview

Here are some last minute tips before your phone interview.

- You’ll be coding, real-time. If you don’t have experience of using them – try them out.
- Coding fluency is prerequisite for the role, so avoid pseudo-code if you can. Your solutions will be shown to senior engineers at a later date, so need to be well-formatted & fully compilable.
- Remember to take edge and corner cases into consideration.
- Understand the importance of unit testing in the engineering environment.
- Approach a large problem by taking it apart into small pieces – the interviewer is as interested in how you approach problems as whether you reach the intended result.
- Don’t give up on problems – maybe ask for advice.
- Be passionate, the interviewer want to know that you love coding and programming, and want to hear that you are passionate about it. Enthusiasm for your work,
- coding and computer science is important to get across.

- It is good to have a headset, as you will be coding over the phone. So practically, it will make the interview easier if you’re not holding a phone and coding at the same time!
- Ask questions, to show you are interested and are analytical, showing that you are thinking about the role, the question, the problem etc..
- Talk through your answer and your coding. We are looking for good programmers, but also people who can explain their thought processes and can describe, analytically what they are doing and their answers.
- Don’t worry if your interview is tough – engineers want to stretch you to see if you can deal with new information as well as what you know.
- Listen to everything the interviewer says as he/she may be trying to give you hints or steer you in another direction.
- The interviewer will ask you a warm up question such as
  1. What project do you want to work on?
  2. What are the differences between [Java](https://helloacm.com/unrolling-loop-in-ccjava-style/) and [C++](https://helloacm.com/c-coding-exercise-permutations/)?
  3. What is the most interesting code you have written?
  4. What projects are you working on now?
- Think about possible answers to these and explain them clearly. You may be asked questions based on your CV, so know your CV well!
- Prepare some questions for the engineer – how does he/she structure their day? / what products have they enjoyed working on? / etc.
- Write down all your favourite algorithms the night before, so they are fresh in your mind.
- Get a good night’s sleep the night before!



## References

1. [Some Telephone Interview Questions for C++/C# Software Enginners](https://helloacm.com/some-telephone-interview-questions-for-c-c-software-enginners/)
2. [C# Questions from Job Agency](https://helloacm.com/c-questions-from-job-agency/)
3. [Last Minute Tips before Phone Interview](https://helloacm.com/last-minute-tips-before-phone-interview/)

