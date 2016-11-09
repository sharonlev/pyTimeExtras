# pyTimeExtras
Time related Extra functionality

##Timer
Timer class provides functionality when dealing with timeouts in loops and the likes

###Suggested uses:

**Prividing a 20 seconds timeout to a loop:**
```python
from timeextras import Timer

timer = Timer(timeout=20)
while not (exit_criteria_met or timer.expired):
  #TODO your code here
```

**extending timer if certain events occur:**
```python
from timeextras import Timer

timer = Timer(timeout=20)
while not (exit_criteria_met or timer.expired):
  #TODO your code here
  if event_should_extend_timer_occured:
    timer.extend_by(10)
```

**restarting timer if certain events occur:**
```python
from timeextras import Timer

timer = Timer(timeout=20)
while not (exit_criteria_met or timer.expired):
  #TODO your code here
  if event_should_restart_timer_occured:
    timer.restart()
```

**logging loop total times:**
```python
from timeextras import Timer

timer = Timer(timeout=20)
while not (exit_criteria_met or timer.expired):
  #TODO your code here
timer.stop()
logger.debug("loop took: %s%s" % (timer, " seconds" if not timer.expired else "") )
```

##StopWatch
StopWatch class provides time tracking functionality

###Suggested uses:

**Tracking time:**
```python
from timeextras import StopWatch

stop_watch = StopWatch()
#TODO your code here
stop_watch.stop()
print "code ran in: %.3fs" % stop_watch
```

**Tracking time over multiple(2) separate iterations:**
```python
from timeextras import StopWatch

stop_watch = StopWatch()
#TODO your code here that is time tracked
stop_watch.stop()
#todo other code not time tracked here
stop_watch.go()
#TODO your code here that needs time tracking
stop_watch.stop()
print "total time measured for relevant code to run: %.3fs" % stop_watch
```

**Tracking individual times:**
```python
from timeextras import StopWatch

stop_watch = StopWatch()
#TODO your code here that is time tracked
stop_watch.part_a.stop()
#TODO your code here that needs additional time tracking from initial start point 
stop_watch.almost_any_name_will_work.stop()
#todo wrap up code also measured
stop_watch.stop()
print "time measured for part_a: %.3fs" % stop_watch.part_a
print "time measured for part_b: %.3fs" % stop_watch.almost_any_name_will_work
print "total time measured: %.3fs" % stop_watch
```
