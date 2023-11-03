# Part 1 - Bugs

* A failure-inducing input for the buggy program, as a JUnit test and any associated code:

```
public class ArrayExamples {
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1]; //This is causing the failure
    }
    return arr; //This is also causing the failure
  }
}
public class ArrayTests {
  @Test
  public void testReversed() {
    int[] input1 = {1,2,3,4};
    assertArrayEquals(new int[]{4,3,2,1}, ArrayExamples.reversed(input1));
  }
}
```

* An input that doesn’t induce a failure, as a JUnit test and any associated code:

```
public class ArrayExamples {
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1]; //This is causing the failure
    }
    return arr; //This is also causing the failure
  }
}
public class ArrayTests {
  @Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
```

* The symptom, as the output of running the tests:

An output from a Failure-inducing input for the buggy program:

<img width="958" alt="Screenshot 2023-11-01 at 12 34 54 PM" src="https://github.com/SamH314/cse15l-lab-reports/assets/146782614/b83d4bdd-a308-4edf-97ab-0e52a82686ba">

An output from an input that doesn't induce a failure for the buggy program:

<img width="321" alt="Screenshot 2023-11-01 at 12 33 08 PM" src="https://github.com/SamH314/cse15l-lab-reports/assets/146782614/29c5cd38-3a11-47b9-aa41-32c5d485d6f2">


* The bug, as the before-and-after code change required to fix it:

```
//before:
public class ArrayExamples {
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
}
```
```
//after:
public class ArrayExamples {
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
}
```
We were not copying the elements from the input array to the new array in reverse order, instead we were putting what was in the new array into the input array and returning the input array. To fix this we made it so that input arr copies down it's elements to the new input. The next fix is making it return `newArray`.

# Part 2 - Researching Commands

The command I choose is `grep`.

Hello Seagull how are you?

1. grep -i <.txt>

*
```
sammyhernandez@Sammys-MacBook-Pro technical % grep -i "PLANES" */chapter-1.txt    
"WE HAVE SOME PLANES"
    They were planning to hijack these planes and turn them into large guided missiles, loaded with up to 11,400 gallons of jet fuel. By 8:00 A.M. on the morning of Tuesday, September 11,2001, they had defeated all the security layers that America's civil aviation security system then had in place to prevent a hijacking. The Hijacking of American 11 American Airlines Flight 11 provided nonstop service from Boston to Los Angeles. On September 11, Captain John Ogonowski and First Officer Thomas McGuinness piloted the Boeing 767. It carried its full capacity of nine flight attendants. Eighty-one passengers boarded the flight with them (including the five terrorists).22 The plane took off at 7:59. Just before 8:14, it had climbed to 26,000 feet, not quite its initial assigned cruising altitude of 29,000 feet. All communications and flight profile data were normal. About this time the "Fasten Seatbelt" sign would usually have been turned off and the flight attendants would have begun preparing for cabin service.
    At the same time, Boston Center realized that a message transmitted just before 8:25 by the hijacker pilot of American 11 included the phrase, "We have some planes."
    Several FAA air traffic control officials told us it was the air carriers' responsibility to notify their planes of security problems. One senior FAA air traffic control manager said that it was simply not the FAA's place to order the airlines what to tell their pilots.
    Controllers track airliners such as the four aircraft hijacked on 9/11 primarily by watching the data from a signal emitted by each aircraft's transponder equipment. Those four planes, like all aircraft traveling above 10,000 feet, were required to emit a unique transponder signal while in flight.
    Before 9/11, it was not unheard of for a commercial aircraft to deviate slightly from its course, or for an FAA controller to lose radio contact with a pilot for a short period of time. A controller could also briefly lose a commercial aircraft's transponder signal, although this happened much less frequently. However, the simultaneous loss of radio and transponder signal would be a rare and alarming occurrence, and would normally indicate a catastrophic system failure or an aircraft crash. In all of these instances, the job of the controller was to reach out to the aircraft, the parent company of the aircraft, and other planes in the vicinity in an attempt to reestablish communications and set the aircraft back on course. Alarm bells would not start ringing until these efforts-which could take five minutes or more-were tried and had failed.
    At 8:24:38, the following transmission came from American 11: American 11: We have some planes. Just stay quiet, and you'll be okay. We are returning to the airport.
    The controller only heard something unintelligible; he did not hear the specific words "we have some planes." The next transmission came seconds later: American 11: Nobody move. Everything will be okay. If you try to make any moves, you'll endanger yourself and the airplane. Just stay quiet.
    Boston Center: . . . as far as the tape, Bobby seemed to think the guy said that "we have planes." Now, I don't know if it was because it was the accent, or if there's more than one, but I'm gonna, I'm gonna reconfirm that for you, and I'll get back to you real quick. Okay? New England Region: Appreciate it.
    Boston Center: Planes, as in plural.
    Boston Center immediately advised the New England Region that it was going to stop all departures at airports under its control. At 9:05, Boston Center confirmed for both the FAA Command Center and the New England Region that the hijackers aboard American 11 said "we have planes." At the same time, New York Center declared "ATC zero"-meaning that aircraft were not permitted to depart from, arrive at, or travel through New York Center's airspace until further notice.
    By 9:25, FAA's Herndon Command Center and FAA headquarters knew two aircraft had crashed into the World Trade Center. They knew American 77 was lost. At least some FAA officials in Boston Center and the New England Region knew that a hijacker on board American 11 had said "we have some planes." Concerns over the safety of other aircraft began to mount. A manager at the Herndon Command Center asked FAA headquarters if they wanted to order a "nationwide ground stop." While this was being discussed by executives at FAA headquarters, the Command Center ordered one at 9:25.
    The mention of a "third aircraft" was not a reference to American 77. There was confusion at that moment in the FAA. Two planes had struck the World Trade Center, and Boston Center had heard from FAA headquarters in Washington that American 11 was still airborne. We have been unable to identify the source of this mistaken FAA information.
    Right after the Pentagon was hit, NEADS learned of another possible hijacked aircraft. It was an aircraft that in fact had not been hijacked at all. After the second World Trade Center crash, Boston Center managers recognized that both aircraft were transcontinental 767 jetliners that had departed Logan Airport. Remembering the "we have some planes" remark, Boston Center guessed that Delta 1989 might also be hijacked. Boston Center called NEADS at 9:41 and identified Delta 1989, a 767 jet that had left Logan Airport for Las Vegas, as a possible hijack. NEADS warned the FAA's Cleveland Center to watch Delta 1989. The Command Center and FAA headquarters watched it too. During the course of the morning, there were multiple erroneous reports of hijacked aircraft. The report of American 11 heading south was the first; Delta 1989 was the second.
    In fact, not only was the scramble prompted by the mistaken information about American 11, but NEADS never received notice that American 77 was hijacked. It was notified at 9:34 that American 77 was lost. Then, minutes later, NEADS was told that an unknown plane was 6 miles southwest of the White House. Only then did the already scrambled airplanes start moving directly toward Washington, D.C.
    The Secret Service logged Mrs. Cheney's arrival at the White House at 9:52, and she joined her husband in the tunnel. According to contemporaneous notes, at 9:55 the Vice President was still on the phone with the President advising that three planes were missing and one had hit the Pentagon. We believe this is the same call in which the Vice President urged the President not to return to Washington. After the call ended, Mrs. Cheney and the Vice President moved from the tunnel to the shelter conference room.
    There is no evidence that NORAD headquarters or military officials in the NMCC knew-during the morning of September 11-that the Andrews planes were airborne and operating under different rules of engagement.
    First, the Langley pilots were never briefed about the reason they were scrambled. As the lead pilot explained, "I reverted to the Russian threat. . . . I'm thinking cruise missile threat from the sea. You know you look down and see the Pentagon burning and I thought the bastards snuck one by us. . . . [Y]ou couldn't see any airplanes, and no one told us anything." The pilots knew their mission was to divert aircraft, but did not know that the threat came from hijacked airliners.
```

*
```
sammyhernandez@Sammys-MacBook-Pro technical % grep -i "adults" */1468-6708-3-1.txt
        Older adults are frequently counseled to lose weight,
        non-smoking older adults have investigated the association
        adults drew similar conclusions [ 7 ] .
        Many healthy older adults report gradual weight gain
        In older adults, risk factors may have a greater effect
        years of being healthy, in a cohort of older adults for
        modification interventions in older adults.
          population-based longitudinal study of 5,888 adults aged
          categories could be combined for older adults. Since
          interventions for older adults who were merely overweight
          adults are the subjects. This is particularly important
          33 34 ] . For older adults, the risks associated with
          outcome for a trial of weight loss in older adults
          found for underweight older adults. Clinical trials whose
        older adults, especially for women. Future efforts to
        no excess risk for older adults who would be classified as
        obese or underweight older adults, and discouraging trials
        that address older adults who are merely overweight.
```

grep -i basically looks for the pattern in the text file and prints the line that it shows up in the text file. This can be useful for trying too look for context of the pattern, when you're also interested on the other characters that are in the same line as the pattern.

2. grep -l

*
```
sammyhernandez@Sammys-MacBook-Pro 911report % grep -l "America" *.txt
chapter-1.txt
chapter-10.txt
chapter-11.txt
chapter-12.txt
chapter-13.1.txt
chapter-13.2.txt
chapter-13.3.txt
chapter-13.4.txt
chapter-13.5.txt
chapter-2.txt
chapter-3.txt
chapter-5.txt
chapter-6.txt
chapter-7.txt
chapter-8.txt
chapter-9.txt
preface.txt
```

*
```
sammyhernandez@Sammys-MacBook-Pro biomed % grep -l "Adults" *.txt 
1471-213X-1-6.txt
1471-2296-3-18.txt
1472-6785-1-3.txt
1472-6963-1-8.txt
rr37.txt
```

grep -l looks for the files that contains the pattern that you are looking for. For the first codeblock, it's showing me that "America" is in chapter 1 all the way through chpater 13. This is useful when you are looking for a word and don't want to check every file to see if it contains that word. Saves you a lot of time.  

3. grep -r

*
```
sammyhernandez@Sammys-MacBook-Pro technical % grep -r "PLANES" 911report   
911report/chapter-1.txt:"WE HAVE SOME PLANES"
911report/chapter-5.txt:            THE "PLANES OPERATION"
```


*
```
sammyhernandez@Sammys-MacBook-Pro technical % grep -r "adults" */1468-6708-3-1.txt
biomed/1468-6708-3-1.txt:        Older adults are frequently counseled to lose weight,
biomed/1468-6708-3-1.txt:        non-smoking older adults have investigated the association
biomed/1468-6708-3-1.txt:        adults drew similar conclusions [ 7 ] .
biomed/1468-6708-3-1.txt:        Many healthy older adults report gradual weight gain
biomed/1468-6708-3-1.txt:        In older adults, risk factors may have a greater effect
biomed/1468-6708-3-1.txt:        years of being healthy, in a cohort of older adults for
biomed/1468-6708-3-1.txt:        modification interventions in older adults.
biomed/1468-6708-3-1.txt:          population-based longitudinal study of 5,888 adults aged
biomed/1468-6708-3-1.txt:          categories could be combined for older adults. Since
biomed/1468-6708-3-1.txt:          interventions for older adults who were merely overweight
biomed/1468-6708-3-1.txt:          adults are the subjects. This is particularly important
biomed/1468-6708-3-1.txt:          33 34 ] . For older adults, the risks associated with
biomed/1468-6708-3-1.txt:          outcome for a trial of weight loss in older adults
biomed/1468-6708-3-1.txt:          found for underweight older adults. Clinical trials whose
biomed/1468-6708-3-1.txt:        older adults, especially for women. Future efforts to
biomed/1468-6708-3-1.txt:        no excess risk for older adults who would be classified as
biomed/1468-6708-3-1.txt:        obese or underweight older adults, and discouraging trials
biomed/1468-6708-3-1.txt:        that address older adults who are merely overweight.
```

grep -r looks for a pattern in every text file from the directory and it's subdirectories. It is extremely useful when looking for a specific word and you're in a directory tree. 

4. grep -c

*
```
sammyhernandez@Sammys-MacBook-Pro technical % grep -c "America" */chapter-1.txt
85
```
*
```
sammyhernandez@Sammys-MacBook-Pro technical % grep -c "adults" */1468-6708-3-1.txt
18
```
grep -c basically counts the number of lines the pattern shows up inside the text file. It can be useful for looking for a textfile that contains the most amount of that patterns refernces. 


I used Chat Gpt for looking up grep command lines.
Prompt:
```
what are some grep commands
```
Response:
```
grep is a powerful command-line utility for searching text using regular expressions. Here are some common grep commands and options:

Basic Search:

grep pattern file: Searches for "pattern" in "file" and displays lines that match.
Recursive Search:

grep -r pattern directory: Searches for "pattern" in all files within "directory" and its subdirectories.
Case-Insensitive Search:

grep -i pattern file: Performs a case-insensitive search for "pattern" in "file."
Invert Match:

grep -v pattern file: Displays lines that do not contain "pattern" in "file."
Line Numbers:

grep -n pattern file: Displays line numbers along with matching lines.
Whole Word Search:

grep -w pattern file: Searches for whole words that match "pattern."
Regular Expression Search:

grep -E 'regex' file: Searches using extended regular expressions defined by "regex."
Count Matching Lines:

grep -c pattern file: Counts the number of lines that match "pattern" in "file."
Display File Names:

grep -l pattern file1 file2 ...: Lists the names of files containing "pattern."
Recursive Display File Names:

grep -rl pattern directory: Lists the names of files containing "pattern" within "directory" and its subdirectories.
Display File Names with Matching Lines:

grep -rl pattern directory | xargs grep pattern: Lists file names and matching lines within "directory" and its subdirectories.
Quiet Mode:

grep -q pattern file: Silences the output and is often used to check if "pattern" is present in "file."
Print Context:

grep -A num pattern file: Prints "num" lines after each match.
grep -B num pattern file: Prints "num" lines before each match.
grep -C num pattern file: Prints "num" lines before and after each match.
These are some of the common grep commands and options. You can combine these options as needed to perform more advanced and specific text searches in your files and directories. Use man grep to access the manual page and learn more about grep and its available options.
```
Prompt:
```
how does grep -c work
```
Response:
```
The grep -c command is used to count the number of lines in a text file that match a specified pattern. Here's how it works:

You provide the grep command with a pattern you want to search for in a file.
grep -c scans the file and counts how many lines contain the specified pattern.
Instead of displaying the matching lines, it returns the count as its output.
Here's the basic syntax:

bash
Copy code
grep -c "pattern" file
For example, if you have a file called example.txt with the following contents:

bash
Copy code
This is a test.
Testing 1, 2, 3.
Test complete.
Another test.
And you run:

bash
Copy code
grep -c "test" example.txt
The output will be 3, because there are three lines in the file that contain the word "test."

grep -c is useful when you want to quickly find out how many lines in a file match a particular pattern, without displaying the actual lines. This can be handy for various scripting and automation tasks where you need to process the count of matching lines.
```
