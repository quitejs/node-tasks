#tasks

write aysnc code more naturaly

#usage

```
npm install quite-tasks
```

#Quick examples
```coffeescript
T = require './tasks'
fs = require 'fs'
T.parallel(
    for file in ['tasks.cf', 'example.cf', 'file3']
          T fs.stat, file
).run (err, results) =>
  for result in results
    if result
      console.log result.size
    else
      console.log 'file not exist'
```
#Documentation
## T(function, args..., cb)
 T is a function to turn plain function invoke into a `Taski` object , make it's invoke under control.

###arguments
* `function` - the function to invoke
* `args...` - arguments
* `cb` - (optional) function to execute after the function invoke

###Example

## T.series(tasks...)
build a series tasks list, a `Series` object

## T.parallel(tasks...)
build a parallel tasks list, a `parallel` object

##Task(function, args..., cb)
Task is the fondmantal Class of `tasks`, simplely hold all information of a function invoke.

##Parallel

##Parallel.limit(limitNum)
only no more than `limitNum` tasks will be simultaneously running at any time.

##Parallel.run(cb)
Run the tasks in parallel

##Series

##Series.circle(circleNum, measurer)
run the first task after finish the last one. `circleNum` is the number of circles to run, `measurer` is a function that when measurer(result) is true, the circle goes to end.

##Series.run(cb)
Run the tasks in series

 
