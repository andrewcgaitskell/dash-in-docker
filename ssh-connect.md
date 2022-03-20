
## setting up ssh access to vm

___do not___ enable os login

find out user name that google has used

login using google console ui

look at user, in my case it was andrew_gaitskell

exit vm

## generate key

ssh-keygen -t rsa -f ~/.ssh/KEY_FILENAME -C USER -b 2048
 
ssh-keygen -t rsa -f ~/.ssh/mykeyfile -C andrew_gaitskell -b 2048

## connect to vm from local machine

ssh -i ~/.ssh/mykeyfile andrew_gaitskell@35.214.5.22

exit

## login from vs code

open command pallet

type - remote ssh login

paste above command line

update ssh config

