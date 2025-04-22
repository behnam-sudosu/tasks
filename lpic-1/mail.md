# mail 
    MTA ===>> mail transfer agent
    qmail ===>> best one and no one hacked this
    apt update && apt install mailutils
    vim /etc/aliases
        behnam: root
    vim .forward ===>> you can see email
    mail behnam@localhost
    cc: reza
    subject: test email
        text
    ctrl + D

    mail ===>> show all emails
    q ===>> quite
    d ===>> delete
    /var/mail/behnam ===>> mailbox
    /home/behnam/mbox ===>> save email here
    mailq ===>> show email dosn't send
    mail -s "test" behnam@localhost ===>> -s set subject here " "
    mail -s "test" behnam@localhost < /home/behnam/file1 ===>> read file
    mail -s "test" behnam@localhost -a /home/behnam/file1 ===>> -a attach file