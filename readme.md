

today,<br/>
day formatting

```
  var today = new Date();
  moment(today).format("MMM DD, YYYY");
  => Apr 25, 2019
  moment(today).format('dddd MMM D')
  => Thursday Apr 25
  moment(today).format('ddd MMM D')
  => Thu Apr 25
  moment(today).format('dd MMM D')
  => Th Apr 25

  // UTC from server
  moment.utc(assignedDate).format('dddd MMM D')
  => Thursday Apr 25
```

today,<br/>
time formatting

```
  var today = new Date();
  moment(today).format('hh:mm A');
  => 12:37 PM

  // UTC from server
  moment.utc(assignedDate).format('hh:mm A');
  => 12:37 PM
```

in 6 days

```
  var today = new Date();
  moment(today).add(6,'days').format("MMM DD, YYYY");
  => May 01, 2019
  var newDay_moment_object = moment(today).add(6,'days');
  newDay_moment_object.format("MMM DD, YYYY");
  => May 01, 2019
```

compare if date sent from server is today<br/>
NOTE because its from server must use .utc()

```
  var dateFromServer = '2019-04-27T00:00:00Z';
  var today = new Date();
  moment.utc(dateFromServer).isSame(today, 'day');
  => false
```

formatting a duration<br/>
NOTE django sends a string '13:15:00' which is (hours, muntes, seconds )the same as the time string on the end of the assignedDate field.

```
  var duartion_in_milliseconds = moment.duration('13:05:00').asMilliseconds();
  => 48000000
  // note that using a lowercase h will round a duration of 13 hours to 1 hour
  moment.utc(duartion_in_milliseconds).format('hh:mm');
  => 01:05
  // note that using a uppercase H will give 13
  moment.utc(duartion_in_milliseconds).format('H:m');
  => 13:5
```


