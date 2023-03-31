# AUX PROJECT 1: SHELL SCRIPTING

>input="/home/ubuntu/shell/names.csv"
>
>while IFS= read -r line

>do

>  sudo useradd -m "$line"

>  sudo usermod -a -G developers "$line"

>  folder="/home/$line/.ssh/"

>if [ -d "$folder" ]

>then

>  sudo cp /home/ubuntu/.ssh/authorized_keys /home/$line/.ssh/authorized_keys

>else

>  sudo mkdir /home/$line/.ssh/

>  sudo cp /home/ubuntu/.ssh/authorized_keys /home/$line/.ssh/authorized_keys

>fi

>done < "$input"