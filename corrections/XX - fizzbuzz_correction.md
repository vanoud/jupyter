limit=0
if [ -z $1 ]
then
        echo "borne haute? "
        read limit

else
        limit=$1
fi

for ((i=0; i<=$limit; i++))
do
        if [[ $i%15 -eq 0 ]]
        then
                echo "FizzBuzz"
        elif [[ $i%3  -eq 0 ]]
then
                echo "Fizz"
        elif [[ $i%5 -eq 0 ]]
        then
                echo "Buzz"
        else
                echo $i
        fi
done
