#!/bin/bash

destination="$HOME/mes_scripts"

get_name() {
if [ -z $1 ]
then
        read -p "Entre le nom du nouveau script $USER: " name
else
        name=$1
fi
}

create_script() {
echo $name
touch $name

echo "#!/bin/bash" >> $name
chmod u+x $name
}

move_script() {
if [[ ! -e $destination ]]
then
        echo $destination
        mkdir $destination
fi

if [[ $destination != "$HOME/mes_scripts" ]]
then
        mv $name $destination/$name
fi
}

open_script() {
nano $destination/$name
}

while getopts 'p:n:' options ;
do
        case "$options" in
                n)
                        name=$OPTARG
                        ;;
                p)
                        destination=$OPTARG
                        ;;
        esac
done

echo $name
echo $destination
get_name $name
create_script
move_script
open_script
