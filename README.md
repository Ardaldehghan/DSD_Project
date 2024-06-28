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

**code implementation**

for implementation of verilog code first we should apply inputs and outputs for verilog module,inputs for the module listed here and how handled them:

1. car_entered: show a car entered to a parking and this signal is asynchron and we don't have any specific priod for applying it,and we handled this signal with always block that works with positive edge of car_entered.
2. is_uni_car_entered: shows entrance car is for professors or for ordinary people,we handled this in if and else case in always block for car_entered and checking if is_uni_car_entered=1 then checking if we have enough capacity in professors part,import them into parking or if is_uni_car_entered=0 vice versa.
3. car_exited: shows exit of car from parking and same as car_entered this signal is asynchron and we don't have any specific priod for applying it,and we handled this with always block that works with positive edge of car_exited.
4. is_uni_car_exited: same as is_uni_car_entered but for exit of the car
5. clk,reset: when reset signal be 1 clock be 8:00 and capacities of parking be in default format,and clk is for times we want to change in capaciteis in hours.

outputs for module listed here:

1. uni_parked_cars: shows total number of professors cars parked in the parking.
2. parked_cars:shows total number of ordinary people cars in the parking.
3. uni_vacated_space:shows total number of vacated_space for proffesors in the parking sum of uni_vacated_space and uni_parked_cars must be equal to all capacity of professors in the parking
4. vacated_space:same as uni_vacated_space but for ordinary people.
5. is_uni_vacated_space:shows we have enough space in our parking for professors.
6. is_vacated_space:shows we have enough space in our parking for ordinary people.

in our implementation we have a register for clock that added to 1 in each #500 delay and in posedge of clk we check if hour be 13 or 14 ,... change somthings in capacities,also we can implement hour in clk,but for confidence we seperate them.


**testing code**

for test it we should make testbench and in testbench check correctness of our module,below we show one of our test benches and some details ,but fully detailed test_benches are in .zip file and show correctness of them in our report.

![alt text](https://imgurl.ir/uploads/b55200_Screenshot_1460.png)
![alt text](https://imgurl.ir/uploads/g617154_Screenshot_1461.png)
![alt text](https://imgurl.ir/uploads/b401654_Screenshot_1462.png)
![alt text](https://imgurl.ir/uploads/i6959_Screenshot_1463.png)
![alt text](https://imgurl.ir/uploads/k662433_Screenshot_1464.png)

in this test first we want to import 250 cars for ordinary people and 250 cars for professors in the parking but for each 5 professor one of them exited from the parking,but because the capacity of ordinary people beofre 13:00 is 200,we can also import 200 of them into the parking,after that we want also import 20 cars of ordinary people and we can't do it,and also after that add 70 professor to parking,but in 14 o clock the capacity for professors be 450 and we exied some cars from professors and can add some ordinary people equal to 50 to it,and also after that in 18 we add (80) some ordinary people to parking and the capacity of professors be euqal to 245,and don't have any vacated space.
