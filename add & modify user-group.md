# add & modify user 
# add & modyfy group

# users

## add
    useradd or adduser (UserName) ===>> add new user
    adduser -m (UserName)===>> make home direcrtory
    adduser -d (UserName) ===>> change home directory
    adduser -c "command" (UserName) ===>> make commant
    adduser -s "/bin/bash" (UserName) ===>> change shell (sh is curent)

## modify
    usermod -c "command" (UserName) ===>> set commant
    usermod -s "/bin/bash" (UserName) ===>> set bash for users
    usermod -L (UserName) ===>> lock the user
    usermod -U (UserName) ===>> unlock the user
    usermod -g (group name) (UserName) ===>> add user to sudo group
    usermod -G (group name) (UserName) ===>> add user to more group
    usermod -aG (sudo) (UserName) ===>> add and append user to group

## delete
    userdel (UserName) ===>> delte user
    userdel -r (UserName) ===>> user delete with directory home
    userdel -f (UserName) ===>> delete file that make this user

#### cat /etc/passwd | grep -i (UserName)


# groups

## add
    useradd -g (GroupName) (UserName) ===>> add user to group
    groupadd (NameGroup) ===>> make group
    group -g "Groupid" (NameGroup)

## modify
    groupmod -n (NewNameGroup) (OldNameGroup) ===>> modify group (-n == name)
    groupmod -g "NewGroupIid" (NmaeGroup) ===>> change group id

## set password
    gpasswd (NameGroup)

## delete
    groudel (NameGroup)

#### cat /etc/group

#### chown (NameUser):(NameGroup) (FileName or DirectoryName)














