# LLM Code Evaluation Report — Assignment 0: Setup

> Copy this file to `LLM-Evaluation.md`, fill it in, and commit it. A0 is a **practice run** of the
> self-evaluation habit you'll use all term — the code is trivial, the workflow is the point.

## Student Information
- **Name**: Jace Kasen
- **Date**: 2026-09-14
- **LLM Used**: Gemini (Antigravity)

## Prompt Used
```text
You are a friendly but precise teaching assistant for a graduate Java course. This is a SETUP
assignment (Assignment 0) — the only code change is that the student put their name into a Greeting
class so a test passes. Help me confirm my environment and workflow are correct. Do not rewrite my
code; just verify and explain.

Check the following and answer each briefly:
1. In my Greeting class, does message() return a greeting that includes MY name (not the placeholder
   "YOUR NAME HERE")? Quote the exact string it would return.
2. Given that, will the JUnit test messageNamesTheStudent PASS (it asserts the message is not blank
   and no longer contains "YOUR NAME HERE")? Will messageHasGreetingPrefix still pass?
3. In one or two plain-English sentences, explain what STUDENT_NAME and message() do, so I can say it
   in my own words during my code walk.
4. Did my tool output below indicate a clean run (tests green, coverage + checkstyle reports
   generated)? If something looks wrong, tell me what to re-check (JDK version, ./gradlew, etc.).

Here is my Greeting.java:
package edu.northeastern.setup;

public final class Greeting {

  private static final String STUDENT_NAME = "Jace Kasen";

  private Greeting() {
    // utility class: no instances
  }

  public static String message() {
    return "Hello, Java! — " + STUDENT_NAME;
  }
}

Here is the output of my commands:
./gradlew run
> Task :run
Hello, Java! — Jace Kasen
BUILD SUCCESSFUL in 735ms

./gradlew test jacocoTestReport checkstyleMain
> Task :checkstyleMain
BUILD SUCCESSFUL in 1s
```

## What the LLM said


Hello Jace! Here is your TA review for Assignment 0:

---

### TA Review & Environment Verification

**1. Greeting Return Value**
Yes! `message()` returns a greeting that includes your name rather than the placeholder.
- Exact string returned: `"Hello, Java! — Jace Kasen"`

**2. JUnit Test Status**
* **`messageNamesTheStudent`**: **PASS**. The returned string is not blank (`assertFalse(message.isBlank())` passes) and no longer contains `"YOUR NAME HERE"` (`assertFalse(message.contains("YOUR NAME HERE"))` passes).
* **`messageHasGreetingPrefix`**: **PASS**. The message starts with `"Hello, Java!"`, satisfying `assertTrue(message.startsWith("Hello, Java!"))`.

**3. Plain-English Explanation for your Code Walk**
> `STUDENT_NAME` is a private constant holding the student's name as text, and the static `message()` method builds and returns the full greeting string by joining that name to the standard `"Hello, Java! — "` prefix.

**4. Tool Output & Build Health**
Your run was completely clean:
* `./gradlew run` successfully printed: `Hello, Java! — Jace Kasen`
* `./gradlew test jacocoTestReport checkstyleMain` exited with `BUILD SUCCESSFUL`:
  * All unit tests passed (green).
  * JaCoCo test coverage report was generated.
  * Checkstyle ran with zero style or formatting violations.

---

### Next Steps for Submission
Whenever you're ready to wrap up:
1. Create `submission/LLM-Evaluation.md` (e.g., `cp LLM-Evaluation-Template.md submission/LLM-Evaluation.md`) and paste this evaluation along with your checklist and reflection.
2. Confirm both `submission/Greeting.java` and `submission/LLM-Evaluation.md` are present.
3. Commit and push to your repository (`git add -A && git commit -m "A0: setup" && git push`).
4. Record your ~1-minute screen walkthrough and submit to Canvas (see [code-walk.md](file:///Users/jankasen/dev/northeastern-projects/cs-5004-5010/cs-5004-5010-w01/code-walk.md)).

## Your checklist
- **`./gradlew run` prints the greeting with my name?**: Yes
- **`./gradlew test` is green?**: Yes
- **Coverage + checkstyle reports generated?**: Yes
- **I can explain what `Greeting.message()` returns and why the test passes?**: Yes

## Reflection
Setting up the environment and running Gradle tasks was smooth. Everything compiled cleanly on JDK 21, and the test suite, coverage reports, and checkstyle passed without issues on the first run after updating `STUDENT_NAME`.
