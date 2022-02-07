#!/bin/bash
alphabet=(a b c d e f g h i j k l m n o p q r s t u v w x y z)
mot=$2
decalage=$1
fin_decalage=$(($decalage-1))
echo $mot | tr "a-z" "${alphabet[$decalage]}-za-${alphabet[$fin_decalage]}"
