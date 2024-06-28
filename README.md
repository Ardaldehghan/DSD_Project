**Parking siumlator:**

This project is a simulator of parking that includes two groups,first group are ordinary people 
and second are proffesors.
we should handle enter and exit cars into the parking and divide capacity between them with rules
that we have for example total capacity is 700 ,or proffesors have priroty to ordinary people.

**tools**

1. verilog

**Parking rules**

we have some rules in the parking now we list them:

1. From 8:00 to 13:00, the capacity is 200 for ordinary people and 500 for professors
2. Between 13:00 and 16:00 every hour, the capacity of professors is reduced by 50 and 50 are added to the normal capacity,but if vacated space of professors in a hour be less than 50 we don't change capacitites on that hour.
3. in 16:00 ,the capacity for ordinary people be 500 and for proffessors be 200,but if parked_cars for professors be bigger than 200 we can't reduce capacity of proffessors to 200 and in this case the capacity for professors after 16 be equal to professors parked_cars and rest from 700 be for ordinary people
