
-loop 1-
[source] free slots [ 
  [ '11:30', '13:30' ], 
  [ '17:30', '17:45' ] 
]
[target] free slots [
  [ '09:00', '09:15' ],   => 11:30 < 9:15 => nil            | 17:30 < 09:15 => nil
  [ '12:00', '14:00' ],   => 12:00 < 13:30 => 12:15 - 13:30 | 17:30 < 14:00 => nil
  [ '16:30', '17:00' ],   => 16:30 < 13:30 => nil           | 17:30 < 17:00 => nil 
  [ '17:30', '19:00' ]    => 17:30 < 13:30 => nil           | 17:30 < 17:45 => 17:30 - 17:45
 ]
free slots [ 
  [ '09:00', '11:30' ],
  [ '12:15', '15:00' ], 
  [ '16:30', '17:45' ] 
]


-loop 2-
[source] free slots [ 
  [ '12:15', '13:30' ], 
  [ '17:30', '17:45' ] 
],
[target] free slots [ 
  [ '09:00', '11:30' ],   => 12:15 < 11:30 => nil           | 17:30 < 11:30   => nil
  [ '12:15', '15:00' ],   => 12:15 < 13:30 => 12:15 - 13:30 | 17:30 < 15:00   => nil
  [ '16:30', '17:45' ]    => 16:30 < 13:00 => nil           | 17:30 < 17:45   => 17:30 - 17:45
]

-final free slots after finding of intersections-
freeSlots [ 
  [ '12:15', '13:30' ], 
  [ '17:30', '17:45' ] 
]

-find possible time for [60 minutes] meeting
freeSlots [ 
  [ '12:15', '13:30' ], => 75 minutes slot => (75 >= 60) => found
  [ '17:30', '17:45' ]  => 15 minutes slot
]

earlist possible time of 60 mins meeting => 12:15