simple splitwise using c++:-

what it do:
user can make a group and add people to it
u can add expenses like who paid and for what
it support split by equal, exact amount and percentage
u can add multiple users in one expense
shows who owe how much to who
also show expense history

what it not do:
no settle up feature for now
no saving to file or database
no proper error handlings
not thread safe or concurrent safe

how to run:
need c++ compiler that support c++11 atleast
g++ -std=c++11 splitwise.cpp -o splitwise
./splitwise

inputs:
program will ask:
name of group
how many users
name of each user
how many expenses

for each expense:
who paid
how much
what for (description)
split type: equal / exact / percentage
how many participants and their names
if exact or percent then amount or % for each

example:
Enter group name: Goa Trip  
Enter number of users: 3  
Alice  
Bob  
Charlie  
Enter number of expenses: 2

Expense 1:  
Paid by: Alice  
Amount: 900  
Description: Hotel  
Split type: equal  
Participants: Alice Bob Charlie  

Expense 2:  
Paid by: Bob  
Amount: 600  
Description: Dinner  
Split type: exact  
Participants: Bob Charlie  
Split amounts: 400 200  

some decisions:
i used unordered_map for storing balances cause it's fast
vector or set will be slow for finding user every time
everything updated during adding expense
users auto-added if not already present

okay so like i used unordered_map cuz it help to get the balance between two users very fast like in O(1) time...
we just give the other person's name and it directly tell how much is owed or paid, no need to search or loop anything
if i used vector or set then i had to go through whole list everytime to find the person and balance which is slow, like not scalable if group have many people...
so hashmap just make everything more easy and quick
