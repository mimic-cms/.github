# Running locally
Bash scripts in root of folder containing cloned repositories:
## install.sh
```bash
#!/bin/bash
dirs=(./admin ./builder ./host)

for D in ${dirs[*]}; do (cd $D && echo "INSTALLING PACKAGES IN: $D" && exec npm i); done
```

## launch.sh
```bash
#!/bin/bash
dirs=(./admin ./builder)

(trap "kill 0" SIGINT
for D in ${dirs[*]}; do
    cd $D && npm run dev &
done
wait)
```
