# Dining Philosophers Demo

## Description

This demo demonstrates multitasking within the VxWorks kernel by providing two
solutions to Dijkstra's famous dining philosophers problem. The main goal
of the problem is to find ways to avoid both deadlock and starvation
when a finite set of actors share a finite set of resources that
can be used by one actor only at a time.

The problem is described as follows: five philosophers sit around a table to
think and eat. Between each adjacent philosopher there is a fork. When a
philosopher is done thinking she/he needs to grab the two forks on his/her
immediate right and left to be able to eat. When the philosopher is done eating
she/he puts down the forks and go back to thinking for a while till he or she
is hungry again, etc., etc.

In this implementation the number of philosophers can be changed (five being
the default). Also the duration of a philosopher's thinking phase is not the
same for all. This brings a more realistic touch to the situation since,
usually, actors accessing a resource do not all have the same frequency of
access to that resource. This implementation simply lets a philosopher think for
a number of seconds equal to the philosopher's order number around the table
(i.e. 1 to x) instead of some random time or an equal amount of time for all.

The two solutions implemented here are 1) a ticket-based one, and 2) a
claim-based one. The ticket-based solution is fair in the sense that all
philosophers get to access the resource for the same amount of time in average
whether they think quick (or shallowy...) or long. The drawback is that the
faster thinkers get to wait more for accessing the resource. The claim-based
solution is addressing this by letting the faster thinkers access the resource
as long as it is not claimed by another philosopher (in which case the
requestor still has to wait until the other philosopher has gotten a chance to
use the resource).

## Sample Output

```
Philosopher 0 EATING
Philosopher 1 THINKING
Philosopher 2 THINKING
Philosopher 3 EATING
Philosopher 4 THINKING
Philosopher 5 THINKING
```
