# Taco Chat Bouc Cheese Pizza

```bash
#!/usr/bin/env bash

nb=${1:-1}

for (( i=0 ; i<nb ; i++)); do
        for element in "taco" "chat" "bouc" "cheese" "pizza"; do
                echo "$element"
        done
done

```
