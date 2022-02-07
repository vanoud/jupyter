
#!/bin/bash

places=5
tours=3
file=(2 3 4 5)
profit=0

avancer_file() {
        temp=${file[@]:0:$1}
        file=(${file[@]:$1})
        file+=("$temp")
}

calculer_profit() {
for i in ${temp[@]}
do
        profit=$(($profit+$i))
done
}

echo ${file[@]}
while [ $tours -gt 0 ]
do
        tours=$(($tours-1))
        if [ $((${file[0]} + ${file[1]})) -le 5 ]
        then
                avancer_file 2
        else
                avancer_file 1
        fi
        echo ${file[@]}
        calculer_profit
done

echo "profit: " $profit

