Event-Driven Programming — School Quiz App

Scenario: A student submits a quiz in an online school system.

---

Event — The student finishes the quiz and clicks the 
"Submit Quiz" button, triggering something for the system to react to.

Event Source — The Submit button on the quiz page is the 
origin of the event — it is what produced and sent out the signal.

Event Listener — The system is constantly watching the Submit 
button in the background, doing nothing until it detects that a click has occurred.

Event Handler — The moment the click is detected, a function immediately runs — 
it collects the student's answers, calculates the final score, and displays "You scored 8/10!" on the screen.

Event Queue — At nearly the same time, the exam timer also runs out and the 
teacher opens the results page. All three events — student submitted, timer 
expired, teacher opened results — line up in a queue and are processed one by 
one in the order they arrived.

Event Loop — The event loop runs silently in the background at all times.
It continuously checks the queue, picks up the next event, sends it to the 
correct handler, and goes back to waiting — keeping the entire system responsive and alive.
