############### DEFINE FUNCTIONS HERE ##############

Usage()
{
  echo "                     USAGE                                  "
  echo " $0 [-d \"Remote Directory Path\"] -f \"Filename-to-upload\""
  echo "-------------------------- or -----------------------------"
  echo " $0 Filename-to-upload"
  exit 1
}

################# ARGUMENTS CHECKING #################

while getopts d:f: choice
do
   case $choice in
   d) Dname=$OPTARG;;
   f) Fname=$OPTARG;;
   esac
done

[ $# -eq 1 ] && Fname=$1
[ -z $Dname ] && Dname="/"                  #change it to suit
[ -z $Fname ] && echo "Bad Arguments" && Usage

[ ! -e $Fname ] && echo "$0: $Fname  no such file" && exit 1

############### DEFINE VARIABLES HERE ################

Server="gestio.bell-lloc.org"               #Remote ftp server.
Username="administrador"                         #Remote ftp user name.
Password="S1stema15963"                   #Remote ftp Password.

# change above to suit

############### MAIN PROGRAM STARTS HERE #############

# Remove comment lines within the here document before run the script

ftp -n $Server <<ServerEnd
user "$Username" "$Password"

# binary command Set the file transfer type to support binary file
# transfer.So you can transfer all type of files.

binary

# hash command is used for printing hash-sign("#") for each data block
# transferred. The size of data block is system dependent.In my box it
# is 1024 bytes. hash command is a toggle switch, by default it is set
# off most systems.

hash                           # comment it if you don't need it

cd $Dname

# pwd command prints current directory on the remote host. This shows
# your file is uploading to which directory.

pwd                            # comment it if you don't need it

put "$Fname"
bye
ServerEnd

exit 0
