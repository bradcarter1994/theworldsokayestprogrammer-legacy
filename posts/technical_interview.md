---
title: 'How to Ace a Technical Interview Question'
author: 'Brad Carter'
date: '6 December 2020'
---

To put it mildly, my first interview with Microsoft didn’t go well. I don’t remember many of the specifics. To be honest with you, I don’t even remember what my interviewer looked like. I can remember the technical question though. It was, “Can you implement the insert method on a linked list?” I can also remember the mistake that kept me for getting a call back. (I updated current.next and new.next in the wrong order.) Above everything else though, I can remember feeling embarrassed that I couldn’t answer a question about a first-year computer science topic and feeling frustrated that I apparently needed to be able to answer any kind of technical question on the spot if I wanted to get a technical internship.

Technical interviews are scary largely because they are unpredictable. The easiest way to make them less scary is to make them more predictable. In the blog post, I'm going to walk through the format that technical interviews typically take at large companies, the types of questions asked that are frequently asked, and strategies for answering them thoroughly and consistently.

Technical interviews at companies like Microsoft, Amazon, and Google tend to follow a similar pattern. For a one-hour, last round interview, you can typically expect
- 10 to 15 minutes of “Tell me about yourself” and soft skill questions
- 30 to 40 minutes of technical problem solving
- A 10 minute break period between interviews

Soft skill questions are ones like "Can you tell me about a time when you had a conflict with a teammate?" or the ever popular "Tell me about a weakness of yours." They are there to help the interviewer understand how well you can work with a team as well as to help you ease into the interview. While soft skill questions can be a major differentiator for candidates with similar technical fortitudes, they are outside the scope of this post and we won't be discussing them further. If you are interested in learning more about soft skill questions and how to answer them, check out the chapter "Behavioral Questions" in Gayle McDowell’s [*Cracking the Coding Interview*](http://www.crackingthecodinginterview.com/).

Technical questions help an interviewer assess a candidate's technical skills and problem-solving abilities. I've found that technical questions generally come in two flavors: algorithmic and architectural questions.

Algorithmic questions ask a candidate to write or complete a function to calculate an output from some inputs or to otherwise implement some behavior. It's especially common for algorithmic questions to ask a candidate to finish implementing a stubbed-out function on a data structure. Examples of algorithmic questions include:
- "Given two strings, can you write some code to determine if those two strings are anagrams of one another?"
- "Can you implement the insert function on an array list?"
- "Can you write a function that determines if a given string is a palindrome?"

On the other hand, Architectural questions ask candidates to give a high-level design for a product or system, typically in pseudo-UML. These questions give candidates the opportunity to show that they can conceptualize a system as a whole and that they can think in end-to-end terms. Some architectural problems that I've been given in interviews include:
- "Please design the back-end system for a theater ticket reservation system that is similar to Fandango."
- "Please design the software control systems for the elevators in a large building."

While answering technical questions like these on a white board can initially seem daunting, we can remove much of the anxiety surrounding them with a little planning and preparation.

I’ve found that the easiest way to make technical questions less scary is to develop a general outline that can be adapted to specific questions on the fly. There are a couple of major advantages to this approach.

First, we, as interview candidates, always know what to say next. While pauses and verbal stumbles are a normal part of any conversation, the perceived stakes in a job interview can make ‘um’s and ‘ah’s feel like major faux pas. An outline can keep us focused, provide direction, and can help us determine if there are still points that we want to talk about on current subject and when it is time to move into the next one.

Second, a solid outline makes it easier to virtue signal and name-drop. Especially for people who just graduated or who are less than a couple of years out of college, a huge part of technical interviews is communicating knowledge of or familiarity with tools, practices, and concepts that are commonly used in industry but which are frequently missed or under-taught in a university program. Having an outline to follow can make it easy to remember to bring up topics like unit tests and version control that are easy to forget in the moment. It also helps us bring the topics up at the appropriate point in the conversation instead of tacking them all on at the end. Even if you don’t have much practical experience with concepts like caching or monitoring and telemetry, just mentioning them can help you differentiate yourself from the rest of the candidate pool.

The following is the rough outline that I use when answering algorithmic technical questions:
1.	Problem Specification
    1.	Problem Definition (Inputs, Outputs, Constraints)
    1.	Clarify Assumptions
    1.	Black Box Test Cases
1.	Solution Implementation
    1.	Best Case Big-O (Big Omega)
    1.	Brute Force Solution
        1.	Optimization
        1.	Eliminate Unnecessary Work
        1.	Eliminate Duplicate Work
    1.	Consider Bottle Necks
        1.	Clean Up
        1.	Version Control
        1.	Monitoring
        1.	Refactoring
        1.	The Pull Request
        1.	Deployment

Let's use one of the algorithmic example questions to watch this outline in action. In this example, I’m going to bold name-dropping topics as I mention them.

>**Interviewer:** Hi, can you write a function for me that can tell if two strings are anagrams of one other?

>**Brad:** Yeah, sure. When I'm starting to work on a problem, I usually like to break my thinking into a specification phase and then an implementation phase. In the specification phase, the first thing I do is try to nail down the problem definition, including the inputs and outputs as well as the constraints. This is also where I try to clarify ambiguities or assumptions with the customer.

>In this problem, the function inputs are two strings, and the output is a Boolean that's true if the two strings can be rearranged into each other and false otherwise. It doesn't look like there are any constraints on the solution beyond the implicit ones to minimize the time and space needed to do the calculation.
(Note that, if there’s a whiteboard in the room, I’m going to be writing these points down in a bulleted list as I am speaking.)

>There are a couple of things that I would like to clarify with the user though.

Clarifying assumptions and ambiguities in the problem statement with the interviewer demonstrates that the interviewee pays attention to details and is also comfortable clarifying unclear requirements with the customer. This habit is important in real-world environments where specifications are frequently vague or changing, and where misunderstanding what is needed in a solution can cause hours or days of re-work.

>**B:** The first thing that I want to clarify is whether we want the anagram check to be case sensitive. For example, do we consider upper case "CAT" to be an anagram of lower case "cat"?

>**I:** Let's assume for simplicity that I’m only going to be calling this function with lower-case strings.

>**B:** Cool. The next thing that I want to clarify is the function needs to be able to handle things like numerics, punctuation, or Unicode characters.

>**I:** Yeah, let's ignore those for right now. We can come back to Unicode characters at the end if we have extra time, but let's just focus on lower-case words without spaces or punctuation for the time being.

>**B:** Great, that simplifies things a lot. Now that we’ve created a problem definition and clarified the problem space, the last thing that I like to do in my specification phase to come up with some test cases for **test-driven development**.

Test driven development is our first major virtue-signaling buzzword and one of the more sought-after practices in big tech, not because it’s always practiced, but because it isn't.

Most engineers have seen a team or two that uses test driven development to great effect, and all engineers have seen teams that either use it poorly or not at all. Signaling that you know what test-driven development is and that you actively practice it is one of the easiest and most effective ways to differentiate yourself from the rest of a candidate pool.

Trying to come up with test cases on the fly can initially seem daunting, but we can outline some common genres of test cases that we can adapt to ensure that we always have a couple that can be easily rattled off. I usually try to come up with examples in this order:
1.	Null and empty value checks (when applicable)
1.	Basic checks for happy and sad paths
1.	Equivalence classes

>**B:** When I'm doing test driven development, I usually start with some basic sanity checks and then work up from there. The most basic things I can think to check in this problem are null values and empty strings. I think that we can reasonably expect that the empty string is an anagram of itself and not an anagram of any non-empty string. For null strings, my gut reaction is that null is not an anagram of anything else, including itself, and that we should through a NullArgumentException if either parameter is null. However, we would definitely want to verify that assumption with the end user.

>**I:** Yeah, that sounds perfectly reasonable to me.

>**B:** Cool, so let’s add some test cases to assert that we want an exception when either parameter is null, and then let’s also assert that “” is an anagram of itself and that ”” is not an anagram of “a”.

>Next, I usually consider basic happy and sad path cases. For this problem, I would want to check that “cat” is an anagram of itself, that “cat” is anagram of “tac”, and that “cat” is not an anagram of “dog”. These are probably sufficient for our basic sanity checks. I would now want to start considering equivalence classes and some more complicated examples. Some equivalence classes that I can think of for anagram include words with the same and different numbers of characters and words with duplicate letters like "aaabbbccc" and "abcabcabc". Wherever possible, it’s important to try to come up with cases in each equivalence class that should make the function return both false and true. At this point, there are still some other avenues that could be explored, but I think that this should be sufficient for our purposes and that we can move onto the solution implementation stage.

>The first thing that I do when I'm designing a solution is a little non-traditional, but I start by thinking about the best possible Big O for runtime and run-space that we could reasonably expect from this solution. I do this first because these best case Big Os will give me a reasonable idea of when I can stop optimizing the solution, which is going to be important in a couple of minutes.
Big O is another major buzzword that interviewers like to hear about. It isn't used terribly frequently in most development jobs, but it's an important principle that demonstrates a solid computer science foundation.

>For this problem I don't think it will be possible to come up with a solution that runs in less than linear runtime or run space in terms of the lengths of the input strings. This is because, at the very least, we'll need linear time to parse the inputs and linear space to store them while we're parsing them.

>Now that we have those best-case scenarios, we can start working on the solution algorithm. I usually start by thinking of the most basic, brute force method of solving to problem and I then try to incrementally optimize that.

Incremental optimization is important for two related reasons:

First, professional software developers usually have more feature requests than they can implement and being able to quickly create a feature that works correctly, even if it isn’t the most efficient possible solution, is an important skill.

Second, there is a temptation to try to impress the interviewer by creating the most efficient solution right off the bat. However, this approach can backfire if a candidate runs out of time before they actually produce something that works. Incremental development allows us to quickly create a working solution and then spend as much (or as little) time as we wish to optimize it, turning an all-or-nothing proposition into something a lot less risky. An inefficient solution that works always wins over an optimized solution that does not.

>**B:** So, anagrams are pairs of words that can be rearranged into one another. For this problem, the most obvious brute force solution is to try to match up the letters of the first word with the letters of the second. Conceptually, we can do this by taking each letter from the first word and iterating over the second word until we find a match. When we find a match, we mark the character in the second word. We could implement this approach by using a bit array to keep track of which letters in the second word are marked. If we can’t find a matching character in the second word for any in the first, or if there are any remaining characters in the second word after we’ve matched all of the characters in the first, then we know that the two words are not anagrams and that we can return false. Otherwise we can return true.

>If we were really building this solution, this would be a good point to code that solution up so that we could check it against our automated test cases. However, since we don't have pseudo-code compiler, we're going to have to rely on our reasoning to tell us that this solution is correct, even though it’s not yet very efficient. Fortunately though, we can now work on optimizing it.

>When I'm optimizing code, I usually look for three patterns: duplicate work, unnecessary work, and bottlenecks. Duplicate work is when we're repeating work unnecessarily, like how we're repeatedly scanning over the second word to find matching characters. We can modify our algorithm to cut out this duplicate work by using a bag (or multi-set) to store the characters from the second word. Instead of iterating over the second word to find matches for the characters of the first, we can instead find and remove characters from the bag in constant time, taking our overall runtime down from quadratic to linear.

>**I:** Hold on for a second. None of the languages that I work with provide bags as an off-the-shelf data structure. Are you going to be providing your own?

>**B:** Yes, we could implement one really easily on top of a hash map or dictionary. Let’s say that that our Bag class has put, pop, and peak methods that insert, remove, and check if an element is contained in the bag respectively. Under the hood, the bag uses a dictionary to map elements to counts. When we put an element in the bag, we add it as a key to the dictionary if necessary and increment it’s count. When we take an element out, we just decrement the count and remove the element from the dictionary if the count goes to zero. Peak would just return the count of an element.

>**I:** Ok, that sounds good.

>**B:** So as I was saying, we could put the characters from the second word into a bag at the start and then just remove a character from the bag for each character in the first word.

>The next pattern that I look for when optimizing is unnecessary work. So far, we’ve been checking if two separate words are anagram by deriving the mapping that we need to rearrange the characters from the first word into the second word. This isn’t strictly necessary for checking if words are anagrams. We could also take advantage of the property of anagrams that the same characters show up in the same counts, which is what allows us to rearrange them.

>Instead of iterating over either word at all, we could actually just insert both words into two separate bags and then compare the bags. The words are anagrams if and only if the character counts in both bags match.

>Inserting the characters into the bags is a linear time operation and the bags use roughly linear amounts of space. While there are probably still a couple of smaller optimizations that we could make, like adding a fast-fail check if the lengths of the inputs aren't the same, we've reached our Big O optimization limits that we defined that the start of the implementation. Assuming that the optimized implementation is still passing all our test cases, we can check our code into version control and begin our cleanup work.

FYI, cleanup work is where we're going to hit a ton of our buzzwords.

>**B:** The next thing that I look at after the algorithm is working is monitoring and telemetry. From where I'm sitting right now, those are probably overkill for a function this simple, but we would also want to double-check with our project manager or user to determine if this is a part of a new feature that we want to be collecting usage data on. Additionally, if we had any kinds of failure cases (like strings with some kind of illegal character for example), we may also want to add metrics to record the strings that are causing the function to error out so that we could later find who is trying to use the function incorrectly.

Monitoring really is overkill for a function this simple but being able to instrument code is a critical skill that is rarely covered in computer science curricula. Like TDD, demonstrating your knowledge of the importance of instrumentation will differentiate you from everyone else who doesn’t mention it.

Checkout James Turnbull’s The Art of Monitoring for a deep dive into how to architect a monitoring infrastructure and how to monitor your applications effectively.

>**B:** The other major part of clean-up is refactoring the code to make it readable and so that it conforms to the team's coding standards. In our case, I think that wrapping each string in a Bag and the comparing the bags is a succinct and eloquent solution. However, it would probably be good to add a clarifying comment explaining the strategy that we're using to test if words are anagrams, since that may not be immediately obvious to someone unfamiliar with the code base. If it's a part of the team coding standard, we would also want to add a docstring, though I personally feel like that would also be overkill.

>Once our code is nice and polished, we can push our changes and open a pull request. After we've resolved any comments and gotten our approvals, we can complete the pull request and merge the branch into main. From there, if we've got a proper CI/CD pipeline set up, our work on this task is done and we can move on to the next work item. If not though, we'll need to create a deployment plan or whatever we need to do on that specific team to move the changes through the dev and UAT environments and finally into production where it can start creating value for the end users. Depending on how thorough our test and monitoring suites are, we may or may not need to watch the changes for hiccups for a couple of days to see if anything concerning crops up. Otherwise, we can move on the next work item.

>Do you have any questions?

Using an outline to answer this example question helped me stay focused and on task while also giving a ton of opportunities to mention topics like automated testing, instrumentation, and code deployment that should effectively differentiate me from the other candidates in my interview pool.

With a little effort, we can modify this outline to also work for architectural questions. The first major difference between architectural and algorithmic questions is that we can expect to spend substantially more time defining the problem (but still in terms of inputs, outputs, and constraints). Depending on your architectural question, it may be wise to list some user profiles and stories to work through how the system will be used and what it needs to be able to do. You can also expect to spend more time clarifying assumptions. For example, if our interviewer had asked us to architect an elevator control system, we would want to follow up with questions like, “Is the control system only responsible for a single elevator, or for a bank of several?” and “Do we need to implement any safety systems, or can we assume that the elevator already know not to move if the door is open?”

We’ll probably spend a similar amount of time talking about testing, but we’ll likely focus more on system-level tests than on functional or unit tests, and out test cases will likely be more user centric as well. In the elevator example, we would probably be looking at tests that check taking a single rider from floor A to floor B, taking several people from one floor to several destination floors, and other similar scenarios.

While we’ll be writing the solution in UML or Entity Relationship Diagrams instead of pseudo-code, we’ll still use incremental development for the same advantages. With architectural problems though, the base solution will probably consist of class or microservice diagrams and the optimizations will consist of questions like where caches could be used to decrease latency and what portions of the system could be replaced with existing off-the-shell solutions.

Finally, I usually end by talking about operation concerns like CI/CD, Monitoring and Telemetry, and Data Management.

In all, my architectural problem outline looks something like this:
1.	Problem Specification
    1.	Problem Definition (Inputs, Outputs, Constraints)
    1.	Clarify Assumptions
    1.	System Tests
1.	Solution Implementation
    1.	Class or Service Diagrams
    1.	Optimization
        1.	Caching
        1.	Off-The-Shelf Substitutions
    1.	Operationalization
        1.	CI/CD
        1.	Monitoring and Instrumentation
        1.	Data Management

My second interview with Microsoft went differently than the first. The format was identical and even the question was of a similar difficulty (“Please write a function that can determine if a string is a palindrome”). The difference was in how I prepared for it. A couple of months before the interview, I had bought a copy of Gayle McDowell’s [*Cracking the Coding Interview*](http://www.crackingthecodinginterview.com/), a whiteboard, and some markers, and I spent 10 to 15 minutes every morning answering a question using variations of the outlines that I’ve laid out in this post.

If you have an upcoming technical interview, the best advice I can give you is to do the same. Get a copy of book and a whiteboard, develop your own outline (you’re welcome to borrow as much as you want from mine 😊), and practice answering a question out loud and on the whiteboard everyday between now and your interview. I think that your results may surprise you.