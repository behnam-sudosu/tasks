# iptables

## general

    iptables
        -A/-I/-D
            -A == APPEND
            -I == INSERT
            -D == DELETE
        -P ===>> chain
        INPUT/OUTPUT/FORWARD
            on what chaine
        -i/-o ===>> what interface, ingoing/outgoin
            input/outpu ===>> ens37
        -s/-d
        source nad destination address
            -s ===>> source ip
            -d ===>> destination ip
        -p ===>> protocol
            tcp/udp/icmp
        --sport/--dport 80
            sorce and destination port
            --sport ===>> going
            --dport ===>> comming
        -j
            ACCEPT/REJECT/DROP/LOG

# temporary

## ipv4
### set rules

    iptables -nvL
    iptables -nvL --line-numbers
    iptables -P INPUT DROP ===>> drop all
    iptables -P OUTPUT DROP ===>> drop all
    iptables -A INPUT -p tcp --dport 22 -j ACCEPT
    iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT
    iptavles -A INPUT -p tcp -s 192.168.1.100 -j DROP
    iptavles -A OUTPUT -p tcp -d 192.168.1.100 -j DROP
    iptables -A INTPUT -p tcp --dport 443 -j ACCEPT

### modules

    iptables -A INPUT -p tcp -m multiport --dport 22,443,3306,21 -j ACCEPT
    iptables -A IOUTPUT -p tcp -m multiport --sport 22,443,3306,21 -j ACCEPT
    iptables -A INPUT -p tcp -m multiport --dport 22,443,3306,21 -d 192.168.10.100/24 -j ACCEPT
    iptables -A INPUT -p tcp -m multiport --sport 22,443,3306,21 -d 192.168.10.100/24 -j ACCEPT
    iptables -A INPUT -p tcp -m limit --limit 100/minute -j ACCEPT
    iptables -A OUTPUT -p tcp -m limit --limit 100/minute -j ACCEPT
    iptables -A INPUT -p tcp -m limit --limit 100/minute --limit-burst 200 -j ACCEPT
    iptables -A OUTPUT -p tcp -m limit --limit 100/minute --limit-burst 200 -j ACCEPT
    iptables -t nat -A PRERUTING -i ens37 -p tcp --deport 8080 -j REDIRECT --to-port 80

## ipv6
### set rules

    ip6tables -nvL
    ip6tables -nvL --line-numbers
    ip6tables -P INPUT DROP ===>> drop all
    ip6tables -P OUTPUT DROP ===>> drop all
    ip6tables -A INPUT -p tcp --dport 22 -j ACCEPT
    ip6tables -A OUTPUT -p tcp --sport 22 -j ACCEPT
    ip6tavles -A INPUT -p tcp -s 192.168.1.100 -j DROP
    ip6tavles -A OUTPUT -p tcp -d 192.168.1.100 -j DROP
    ip6tables -A INTPUT -p tcp --dport 443 -j ACCEPT

### modules

    ip6tables -A INPUT -p tcp -m multiport --dport 22,443,3306,21 -j ACCEPT
    ip6tables -A IOUTPUT -p tcp -m multiport --sport 22,443,3306,21 -j ACCEPT
    ip6tables -A INPUT -p tcp -m multiport --dport 22,443,3306,21 -d 192.168.10.100/24 -j ACCEPT
    ip6tables -A INPUT -p tcp -m multiport --sport 22,443,3306,21 -d 192.168.10.100/24 -j ACCEPT
    ip6tables -A INPUT -p tcp -m limit --limit 100/minute -j ACCEPT
    ip6tables -A OUTPUT -p tcp -m limit --limit 100/minute -j ACCEPT
    ip6tables -A INPUT -p tcp -m limit --limit 100/minute --limit-burst 200 -j ACCEPT
    ip6tables -A OUTPUT -p tcp -m limit --limit 100/minute --limit-burst 200 -j ACCEPT
    ip6tables -t nat -A PRERUTING -i ens37 -p tcp --deport 8080 -j REDIRECT --to-port 80


## permanent
 
    sudo apt install iptables-persistent
    vim /etc/iptables/rules.v4
    iptables-restore < /etc/uptables/rules.v4
    iptables-save > /etc/iptables/rules.v4
    vim /etc/iptables/rules.v6
    ip6tables-restore < /etc/uptables/rules.v6
    ip6tables-save > /etc/iptables/rules.v6

