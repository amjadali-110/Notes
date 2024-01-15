# Table of Content:-
- Enumerate Subdomains via ASN
- Subfinder Tool
- knockpy Tool
- Third Party Websites & Other Tools



### Method 1:- Enumerate Subdomains via ASN


1. Run the following command you will get the ip's:-
```bash
whois -h whois.radb.net -- '-i origin AS6185' | grep -Eo "([0-9.]+){4}/[0-9]+" | uniq -u`
```

whois is a command-line utility for querying WHOIS databases to retrieve information about IP addresses or domain names.
- -h whois.radb.net specifies the WHOIS server to query.
- -- '-i origin AS6185' is used to pass the query -i origin AS6185 to the WHOIS server. This query is specific to finding IP prefixes associated with Autonomous System Number (ASN) 6185.
- grep -Eo "([0-9.]+){4}/[0-9]+" extracts IPv4 address prefixes (CIDR notation) from the WHOIS response.
- uniq -u filters out duplicate entries and displays only unique IP prefixes.


-------------------------------------------------------------------------------------------------------------------------------------------------------

2. **Use https://github.com/j3ssie/metabigor Tool To get IP's**
```bash
# discovery IP of a company/organization
echo "company" | metabigor net --org -o /tmp/metabigor.txt
```


-------------------------------------------------------------------------------------------------------------------------------------------------------

3. **Now Pick any ip save it in ip.txt file and run the following command to enumerate the subdomains:-**
```bash
cat ip.txt | mapcidr -si -silent -o ipscat | hakrevdns -t 100 -d | anew asn_domains.txt
```
- cat ip.txt reads the content of the file ip.txt.
- mapcidr -si -silent -o ipscat ips.txt takes the IP addresses from ip.txt, aggregates them into CIDR notation, and outputs them to a file named ipscat.
- hakrevdns -t 100 -d performs reverse DNS lookups on the IP addresses provided, with a timeout of 100 milliseconds.
- anew domains.txt.txt appends the results of reverse DNS lookups to the file domains.txt.


-------------------------------------------------------------------------------------------------------------------------------------------------------

### Method 2:- Subfinder Tool
```bash
- subfinder -dL scope.txt -all -v | tee subfinder.txt
```

-------------------------------------------------------------------------------------------------------------------------------------------------------

### Method 3:- knockpy Tool

```bash
knockpy target.com --dns 8.8.8.8 
```

The command knockpy domain.com --dns 8.8.8.8 is using the knockpy tool to perform subdomain enumeration on the target domain "domain.com" while specifying a custom DNS server, in this case, "8.8.8.8." Let's break down what this command is doing and its benefits in detail:

1. Subdomain Enumeration:
knockpy domain.com: This part of the command tells knockpy to perform subdomain enumeration on the target domain "domain.com." Subdomain enumeration involves finding subdomains associated with the main domain.

2. Using Custom DNS Server:
--dns 8.8.8.8: This part of the command specifies a custom DNS server to be used for the enumeration process. In this case, "8.8.8.8" is Google's public DNS server.


> Most Popular DNS:-

- Google DNS addresses: 8.8.8.8
- CloudFlare DNS addresses:
1. Primary DNS: 1.1.1.1
2. Secondary DNS: 1.0.0.1
- Amazon CloudFront DNS addresses:
1. Primary DNS: 205.251.192.0
2. Secondary DNS: 205.251.194.0

*Note:-* Chatgtp prompt for More Private DNS
- Are there more dns like google 8.8.8.8 we can use for recon on tools like knockpy



-------------------------------------------------------------------------------------------------------------------------------------------------------


## Method 4:- Third Party Websites & Other Tools

- Shodan:- https://github.com/SmoZy92/Shodomain
```
python shodomain.py <api_key> <target.com>
```

- Censys:- https://github.com/christophetd/censys-subdomain-finder
```
python censys-subdomain-finder.py <target.com>
```

- Github:- https://github.com/gwen001/github-subdomains

##### Websites
- Virustotal:- https://www.virustotal.com/gui/domain/<target.com>/relations
- Shrewdeye:- https://shrewdeye.app/search/<target.com>
- Secrash:- https://www.secrash.com/p/subdomain-scanner.html
- Seckrd:- https://seckrd.com/subdomain-finder.php


-------------------------------------------------------------------------------------------------------------------------------------------------------


## Method 5:- some more ways

- DNSRECON Tool:- ```python dnsrecon.py -n <name_server> -d <target.com> -D subdomains-top1mil-20000.txt -t brt -a -s -b -y -k -w -z```
- DIG:- ```dig +multi AXFR @<name_server> <target.com>```
- ZONE WALKING NSEC DIG:- ```dig +short NSEC <target.com>```

*To know name_server:-* ```dig <domain> -t ns```







sed 's/^https\?:\/\///' alive_subs.txt > without_protocol_alive_subs.txt



>> Origin IP
https://infosecwriteups.com/origin-ip-found-d-dos-waf-cloudflare-protection-bypassed-41fc280ccf8f
https://github.com/Dheerajmadhukar/Lilly
